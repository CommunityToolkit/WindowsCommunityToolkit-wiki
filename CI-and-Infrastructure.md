## CI Processes

### Azure Pipelines
The [Azure instance](https://dev.azure.com/dotnet/CommunityToolkit) runs all of our CI processes. Our Azure pipelines configuration is found at the root of the project, [azure-pipelines.yml](https://github.com/CommunityToolkit/WindowsCommunityToolkit/blob/main/azure-pipelines.yml)

**Jobs** are specified in the pipelines config. The status and results of jobs are reported as [Github Checks](https://docs.github.com/en/github/collaborating-with-pull-requests/collaborating-on-repositories-with-code-quality-features/about-status-checks). The status and results of individual steps for each job are visible on azure ( usually directly linked to in Github Checks ).

### Cake
A lot of the pipeline jobs make use of [Cake Tasks](https://cakebuild.net/docs/writing-builds/tasks/) defined in [build/build.cake](https://github.com/CommunityToolkit/WindowsCommunityToolkit/blob/main/build/build.cake). Cake Tasks are invoked threw [build/build.ps1](https://github.com/CommunityToolkit/WindowsCommunityToolkit/blob/main/build/build.ps1) in the pipelines config and the various task can be ran from powershell using the **Target** option, for example `.\build.ps1 -Target UpdateHeaders`. It is recommended that the build scripts are invoked from the build directory.