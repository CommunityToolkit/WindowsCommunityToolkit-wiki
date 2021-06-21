# Testing

The Toolkit relies on two main test projects to help ensure that we can maintain existing components contributed by the community. Every new feature integrated into the Toolkit should have some form of tests associated with it to ensure future changes to the platform or the Toolkit won't break components.

Our two main test projects are in the `UnitTests` and `UITests` folders and provide three different forms of testing capabilities.

This document explains what these different types of test are and what they're good for, how to run them, and how to add a new tests to the toolkit. 

When developing a new component you should think about what types of tests (or combination) you'll need:

 * **Unit Tests** are good for pure functional code that takes simple inputs and provides deterministic outputs. These can be run in both a .NET environment and a UWP environment. We use a fairly standard MSTest setup to perform our unit tests.
   * **VisualUITestBase** is a sub-class of UWP-based unit test available when realizing a full UI object is required and provides introspection to the VisualTree and layout behaviors. This type of test is good for Panels and layout algorithms or validating the expected behavior of simple UI operations.   
 * **UI Tests** we have built off the same infrastructure that WinUI uses to test their components, which uses the [Windows Apps Test Library](https://github.com/microsoft/Microsoft.Windows.Apps.Test) (the basis of [WinAppDriver](https://github.com/Microsoft/WinAppDriver)). We use the underlying library instead to help facilitate possible control test transitions to WinUI itself. These types of tests are more involved to write, but provide end-to-end testing in a real-world environment; especially when needing to simulate user input is required.

## Unit Tests

[MSTest](https://github.com/Microsoft/testfx) powers our unit tests both locally and in our CI builds in DevOps. You should expect the same behavior in both environments. However, we do test in both .NET and UWP environments for some tests in case we hit edge scenarios with the underlying runtime engine for .NET. In the future, we hope to be unified on .NET 6+ when we fully migrate to WinUI 3 later.

### Test Environments

Unit tests can be run in both a .NET and a UWP environment by placing tests in the `UnitTests.Shared` project. For tests which should only run in a UWP context (either because of WinRT APIs or needing the `VisualUITestBase`), place them in the `UnitTests.UWP` project.

### Running Tests

Tests can easily be run from Visual Studio by opening the `Test Explorer` pane from the `Test` menu. Then just click the Double-Run/Play icon within the pane to run the tests. This will also deploy and run all tests, including the UI Tests (see more below).

To run a specific set of tests (or individual test), just click on the branch within the tree and click the single run/play icon instead.

### Writing a Test

Adding a new unit test is the same as adding any MSTest. There are plenty of existing examples within the repo to show various operations at work. The main thing to ensure is if you're adding the new test class to the right project, either Shared for pure .NET based tests, or UWP for WinRT API tests or Visual tests.

Be sure to mark your test method with `[TestMethod]` for a standard unit test. This will be the only one you'll use in the Shared project type.

### UI Thread Access and VisualUITestBase

For UWP tests, you may also use `[UITestMethod]` if you need to ensure your test runs on the UI Thread. **Note** however, this will not fully realize a created UI element.

You may want to inherit your class from `VisualUITestBase` instead if you need the component to be fully realized within the UI, perform layout, or access the Visual Tree.

After inheriting from `VisualUITestBase` mark your method with the regular `[TestMethod]` declaration as well as making it return `async Task`. This will enable you to call `await App.DispatcherQueue.EnqueueAsync(async () => { ... });` to access the UI thread. You can then call `await SetTestContentAsync(...)` within this method to setup whichever UI component you need within your test page.

To setup your UI element, you can construct it manually or call `XamlReader.Load` with an XML string to represent your test setup.

### Good Testing Practices

It is important to test a variety of scenarios when implementing a component. These should cover not just success scenarios, but failure scenarios and edge cases as well. Try and think about how your component shouldn't be used and right tests to ensure guards against that work as intended or exceptions are thrown.

Use `[ExpectedException]` and `[DataRow]` attributes to help you easily test exceptions or a variety of scenarios with the same test code.

When fixing a bug, it can also be handy to write a unit test first which shows the broken scenario, and then validate the bug is fixed by writing the solution against the same test (which should now pass).


## UI Tests (Integration Testing)

UI Integration tests are useful for testing controls and other helpers that require an actual physical application's UI to be present. i.e. being able to click on a button, see containerized items, or perform complex E2E scenarios across multiple elements of a control.

Before going the route of writing a UI Test, see if the `VisualUITestBase` (above) can suit your needs. That type of test will be easier to write and debug than delving into a UI Test. However, a simple UI Test which loads some sample or scenario of your component and validates basic parts of it can be extremely useful still.

### How to run Integration Tests

The UI integration tests automatically run as part of our continuous integration system on every PR, but you can also run them locally within Visual Studio. They actually get run with all the other Unit Tests within the Visual Studio **Test Explorer**! You can run just the integration tests by selecting the `UITests.Tests.MSTest` node in Test Explorer.

It is important to note though that when the tests run in Visual Studio and the CI they'll actually be run with two different types of harnesses (MSTest locally and [TAEF](https://docs.microsoft.com/windows-hardware/drivers/taef/) in the CI). If you're seeing an issue in the CI, but not in Visual Studio, it may be useful to run a full build locally using the build script of the `build` directory of the repo to replicate a full CI build. In a VS Dev command prompt, you can run `build.ps1 -target=UITest` after a build to run the UI Tests.

### Adding a UI Integration Test

In the `UITests\UITests.Tests.Shared` project folder there is a `Examples` folder containing `SimpleTest.cs`, `SimpleTestPage.xaml`, and `SimpleTestPage.xaml.cs`. 🚨 It is important to use **File Explorer** for this step as Visual Studio will corrupt the special wildcards we use for this project structure.

Copy these files to your desired location within the `UITests\UITests.Tests.Shared` folder and rename them to your liking. However, all Test classes **must** end in `Test.cs` and UI pages in `Page.xaml` and `Page.xaml.cs` for the code-behind. This allows them to be loaded in their respective applications for the test harness and the test app, respectively.

After performing the copy and rename, refresh the `UITests.Tests.Shared` project. You should see your new folder and files automatically appear.

### How the UI Integration Tests Work

The UI tests are made of two components, a **harness** and a **host**. These are two independent processes which comprise the test environment. The **harness** is a standard .NET testing environment (executed with [MSTest](https://github.com/Microsoft/testfx) in VS or [TAEF](https://docs.microsoft.com/windows-hardware/drivers/taef/) in the CI). The **host** is a UWP application which hosts the desired test pages/components to be tested. The **harness** then controls the host application via UI Automation and an **AppService** communication pipe (_or **GRPC** for WinUI 3_).

This means your test code does not have direct access to the UI components and instead must be a set of instructions for user interaction (move mouse, click) to drive the component within the hosting app. This better simulates real-world usage of the component for more complete testing of complex scenarios. You can use things like the `KeyboardHelper` and `InputHelper` to see how you can simulate user inputs.

We use a shared project to help better organize both half of these tests. You'll see both sides of your test together in Visual Studio (the test harness code in your _Test.cs_ file and the hosted page code in your _.xaml/.xaml.cs_ file). But during compilation, these two parts are actually split with the _Test.cs_ file being compiled into the corresponding MSTest/TAEF test harness runner application and the _xaml_ file being compiled into the UWP application.

When the tests are executed, it deploys and runs the UWP app first (you'll see a PowerShell window open when running the tests in Visual Studio). The test harness test suite is then executed by Visual Studio using MSTest or the CI using TAEF to load the appropriate test page for the test to be executed and then run the test code and validate results.

In addition to the base WinUI setup for these tests, we added an additional communication pipe between the test harness and host applications. This allows us for more direct control of loading the test pages, providing an output/logging channel from code executed in the host environment, as well as the ability to request code to be executed for more direct inspection of the host app (e.g. the Visual Tree).
