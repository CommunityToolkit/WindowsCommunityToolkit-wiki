# CI Pipeline
An [Azure instance](https://dev.azure.com/dotnet/CommunityToolkit) runs our CI pipeline.
Our Azure pipelines configuration is found at the root of the project, [azure-pipelines.yml](https://github.com/CommunityToolkit/WindowsCommunityToolkit/blob/main/azure-pipelines.yml)

**Jobs** are specified in the pipelines config.
The status and results of jobs are reported as [Github Checks](https://docs.github.com/en/github/collaborating-with-pull-requests/collaborating-on-repositories-with-code-quality-features/about-status-checks).
The status and results of individual steps for each job are visible on azure ( usually directly linked to in Github Checks ).

Jobs can be added and modified in the pipelines config file.
Checkout the [Azure Pipelines Doc](https://docs.microsoft.com/en-us/azure/devops/pipelines/?view=azure-devops) for more info.

The CI pipeline get triggered to run on `main`, `dev/*` or `rel/*` branches when new commits get pushed to or PRs are opened targeting those branches.

### Cake
A lot of the pipeline jobs make use of [Cake Tasks](https://cakebuild.net/docs/writing-builds/tasks/) defined in [build/build.cake](https://github.com/CommunityToolkit/WindowsCommunityToolkit/blob/main/build/build.cake).
Cake Tasks are invoked through [build/build.ps1](https://github.com/CommunityToolkit/WindowsCommunityToolkit/blob/main/build/build.ps1) in the pipelines config, and the various tasks can be ran from powershell using the **Target** option, for example `.\build.ps1 -Target UpdateHeaders`.
It is recommended that the build scripts are invoked from the build directory.

Cake tasks can be added to the cake file, either to be executed directly from the pipelines config or to be invoked manually.
Also any task can be added as a dependency to another Task.
When `.\build.ps1` is ran (without any options), it runs the Task "Default" and thus all its dependencies.
This task if not typically used in the build pipeline, but it is useful for locally running a most of the CI pipeline locally in order to test changes locally without having to wait on the CI Server. 

## CI Tasks
The CI pipeline performs five tasks when triggered to run on a branch.

### Check formatting
Various formatting checks are run very early on in the CI pipeline.
Currently we verify that all `*.cs` files contain the .NET Foundation license at the top of the file and we check all `*.xaml` with XAML Styler.

### Build
All our projects are built - this includes libraries, tests, and the Sample app.
While this step is primarily used to feed into the package build process, it also makes sure that there are not compilation issues with the libraries, as well no compilation issues with the sample app.
This helps make sure that the sample app is always an accurate example of using the libraries.

### Test
Once all the libraries are built, our tests are ran - see [Testing](https://github.com/CommunityToolkit/WindowsCommunityToolkit/wiki/Testing).

### Publish
The libraries are packaged into NuGet packages and automatically published to our Azure Feeds - see [Preview Packages](https://github.com/CommunityToolkit/WindowsCommunityToolkit/wiki/Preview-Packages).

### Analyze
We perform analysis on the changes in the size of packages, as well as how much the sizes of apps using these packages change.