If this is your first time contributing to Windows Community Toolkit and never created a PR before, do not worry because you are not in this alone. By following [Github Help](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request) guidelines you will be able to create your first Pull Request.

Anyone with write access can create a Pull Request by forking the Windows Community Toolkit repository. Here is how you can [Create a Pull Request from fork](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request-from-a-fork)

Once you fork the Windows Community Toolkit repo, it is essential to create all changes in the feature branch of your forked repository. If you have the changes in the forked feature branch you can create a Pull Request in the main Windows Community Toolkit where your changes will be merged to the main branch. 

:warning: **We will not merge the PR to the main repo if your changes are not in the feature branch of your forked repository** :warning:
 
Once the PR is created and submitted, we will be able to see the associated PR issue and will assist and provide feedback if necessary.

If you are not certain about the Pull Request submitted; our team along with the community members are here to review the work and highlight any changes the PR might require to fulfill any required obligation.

**Submit PullRequest**

For every contribution, you must:
* Test your code with the supported SDKs
* Follow the quality guidance, general rules, and naming convention
* Target main branch (or an appropriate release branch if appropriate for a bug fix)
* Follow the Windows Community Toolkit PR Template 
* If adding a new feature
  * Before starting coding, you should open an issue and start discussing with the community to see if your idea/feature is interesting enough.
* Add or update a sample for the Sample app
  * If creating a new sample, create a new icon by following the Thumbnail Style Guide and templates
*Add or update unit tests (if applicable)
PR must be validated by at least two core members before being merged.

Please make certain that the PR successfully passes all three status check requirements including Toolkit-CI, WIP, license/cla. If it fails and you are aware of the reasoning please fix the error. If you are unaware of the reasoning please escalate by commenting in the PR, and someone from the team will investigate the build error. 

If the PR passes all the requirements above and reviewers have signed off, the PR will be merged. 

Once merged, you can get a pre-release package of the toolkit by adding this ([Azure DevOps feed](https://pkgs.dev.azure.com/dotnet/WindowsCommunityToolkit/_packaging/WindowsCommunityToolkit-MainLatest/nuget/v3/index.json) | [Gallery](https://dev.azure.com/dotnet/WindowsCommunityToolkit/_packaging?_a=feed&feed=WindowsCommunityToolkit-MainLatest)) to your Visual Studio.
