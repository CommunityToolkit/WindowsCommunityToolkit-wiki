The Community Toolkit has a variety of ways to test out new features or fixes ahead of their official release. This page describes the various channels available and how to connect them to your development environment.

🚨 It's important to note that with any of these previews, there are APIs, controls, or features which may change or be removed before the final release. They are intended to make it easier for developers to provide feedback on them ahead of time so we can gauge interest or ensure they cover a broad range of scenarios before we ship them. Therefore, it's important to not rely on the preview package too heavily or use within production software without understanding these risks.

# 'Official' Preview Packages

As we prepare for an official release, we may release 'official' preview packages to NuGet itself, this allows us to more easily reach a broader audience with a scoped set of updates we want developers to try out before we ship. This allows us to gather feedback and make changes before we 'lock them in' for a release.

To access these previews, you can simply ensure you have the [Include prerelease](https://docs.microsoft.com/en-us/nuget/create-packages/prerelease-packages#installing-and-updating-pre-release-packages) checkbox checked in Visual Studio. This will search and display any preview packages in the version dropdown for Windows Community Toolkit [[NuGet Packages]]. We typically use the suffix `-preview` for any of these releases.

# Azure Feeds

We have a number of public NuGet feeds hosted from our Azure DevOps pipeline. These are not found by default when searching the main NuGet server from within Visual Studio. You must add alternate [Package sources](https://docs.microsoft.com/en-us/nuget/consume-packages/install-use-packages-visual-studio#package-sources) within the Visual Studio settings or if sharing within a team/project setup [packageSources](https://docs.microsoft.com/en-us/nuget/reference/nuget-config-file#packagesources) within a `nuget.config` file.

## Latest 🌙

Feed URL: `https://pkgs.dev.azure.com/dotnet/CommunityToolkit/_packaging/CommunityToolkit-MainLatest/nuget/v3/index.json`

The Latest feed is updated whenever a change is merged to the main branch. It contains the latest changes to the next versions of the Community Toolkit. It is a great feed to help test the latest set of features which have gone through the development process and are pending release. (_Note: It is possible new features can still be changed or removed before a release._)

## Toolkit Labs 🧪

Feed URL: `https://pkgs.dev.azure.com/dotnet/CommunityToolkit/_packaging/CommunityToolkit-Labs/nuget/v3/index.json`

The [[Toolkit Labs]] feed contains various _**experimental**_ projects that are being incubated by the community. This feed is provided as an easy way to pull them into projects to test out and provide feedback to their developers. Projects either have their own dedicated repository or come from a central general Lab repo (per technology), but they all push to this feed. See the [[Toolkit Labs]] page in this wiki for more details on our current experiments and where to find more information.

## Pull Requests 🚧

Feed URL: `https://pkgs.dev.azure.com/dotnet/CommunityToolkit/_packaging/CommunityToolkit-PullRequests/nuget/v3/index.json`

🚨 The Pull Request feed is automatically built from PRs that are submitted. They may contain untested features, unreviewed fixes, and code which has not been validated. It is important to understand these risks before pulling a package from the feed.

That said, the Pull Request feed is a great feed to help other developers test and review their features before they are added to the Toolkit. To find the appropriate package version, just check for the last successful build of the PR at the bottom of the page in the PR checks. You can expand it by clicking on `Show all checks` and then finding the version next to the `Toolkit-CI` check, as seen here:

![Expanded PR Checks with Build Number](images/Preview-Packages-PR-Checks.png)

📝 Note, the package in the feed will have a '.g' replacing the '+' seen in this visual for the PR. [See Nerdbank Docs here](https://github.com/dotnet/Nerdbank.GitVersioning/blob/master/doc/dotnet.md).

## WinUI 3 Previews (Archive)

⚠ Note: Stable versions of these packages aligned with the Windows App SDK have been released and are available on NuGet now, find latest information [here](https://aka.ms/wct-winui3).
