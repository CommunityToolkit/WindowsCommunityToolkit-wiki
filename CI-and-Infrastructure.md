# CI Pipeline
An [Azure instance](https://dev.azure.com/dotnet/CommunityToolkit) runs our CI pipeline. Our Azure pipelines configuration is found at the root of the project, [azure-pipelines.yml](https://github.com/CommunityToolkit/WindowsCommunityToolkit/blob/main/azure-pipelines.yml)

**Jobs** are specified in the pipelines config. The status and results of jobs are reported as [Github Checks](https://docs.github.com/en/github/collaborating-with-pull-requests/collaborating-on-repositories-with-code-quality-features/about-status-checks). The status and results of individual steps for each job are visible on azure ( usually directly linked to in Github Checks ).

The CI pipeline get triggered to run on `main`, `dev/*` or `rel/*` branches when new commits get pushed to or PRs are opened targeting those branches.

### Cake
A lot of the pipeline jobs make use of [Cake Tasks](https://cakebuild.net/docs/writing-builds/tasks/) defined in [build/build.cake](https://github.com/CommunityToolkit/WindowsCommunityToolkit/blob/main/build/build.cake). Cake Tasks are invoked threw [build/build.ps1](https://github.com/CommunityToolkit/WindowsCommunityToolkit/blob/main/build/build.ps1) in the pipelines config and the various task can be ran from powershell using the **Target** option, for example `.\build.ps1 -Target UpdateHeaders`. It is recommended that the build scripts are invoked from the build directory.

## CI Tasks
The CI pipeline preforms five tasks when triggered to run on a branch.

### Check formatting
Various formatting checks are run very early on in the CI pipeline. Currently we verify that all `*.cs` files contain the .NET Foundation license at the top of the file and we check all `*.xaml` with XAML Styler.

### Build
All our projects are built, this includes libraries, tests, and the Sample app. While this step primarily to feed into building the packages, it also makes sure that there are not compilation issues with the libraries, as well no compilation issues with the sample app. This helps make sure that the sample app is always an accurate example of using the libraries.

### Test
Once all the libraries are built the our tests are ran, see [Testing](Testing.md).

### Publishing
The libraries are packaged into NuGet packages and automatically published to our Azure Feeds, see [Preview Packages](https://github.com/CommunityToolkit/WindowsCommunityToolkit/wiki/Preview-Packages).

### Package analysis
We perform analysis on the changes of in size of packages as well how much the sizes of apps using these packages change.