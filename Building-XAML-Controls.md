We encourage developers to follow the following guidelines when submitting Pull Requests for controls:

* Your control must be usable and efficient with the keyboard only.
* Tab order must be logical.
* Focused controls must be visible.
* Action must be triggered when hitting the Enter key.
* Do not use custom colors but instead rely on theme colors so high contrasts themes can be used with your control.
* Add AutomationProperties.Name on all controls to define the control’s purpose (Name is minimum, but there are some other things too that can help the screen reader).
* Don't use the same Name on two different elements unless they have different control types.
* Use Narrator Dev mode (Launch Narrator [WinKey+Enter], then CTRL+F12) to test the screen reader experience. 
* Is the information sufficient, meaningful, and helps the user navigate and understand your control.
* Ensure that you have run your XAML file changes through Xaml Styler (version 2.3+), which can be downloaded from [here](https://marketplace.visualstudio.com/items?itemName=NicoVermeir.XAMLStyler). Do not worry about the settings for this as they are set at the project level (settings.xamlstyler).

You can find more information about these topics [here](https://docs.microsoft.com/en-us/archive/blogs/winuiautomation/building-accessible-windows-universal-apps-introduction)

This is to help as part of our effort to build an accessible toolkit (starting with 1.2)
