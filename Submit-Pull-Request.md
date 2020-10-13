For every contribution, you must:
* Test your code with the supported SDKs
* Follow the quality guidance, general rules, and naming convention
* Target master branch (or an appropriate release branch if appropriate for a bug fix)
* Follow the Windows Community Toolkit PR Template 
* If adding a new feature
  * Before starting coding, you should open an issue and start discussing with the community to see if your idea/feature is interesting enough.
* Add or update a sample for the Sample app
  * If creating a new sample, create a new icon by following the Thumbnail Style Guide and templates
*Add or update unit tests (if applicable)
PR must be validated by at least two core members before being merged.

Please make certain that the PR successfully passes all three status check requirements including Toolkit-CI, WIP, license/cla. If it fails and you are aware of the reasoning please fix the error. If you are unaware of the reasoning please escalate by commenting in the PR, and someone from the team will investigate the build error. 

If the PR passes all the requirements above and reviewers have signed off, the PR will be merged. 

Once merged, you can get a pre-release package of the toolkit by adding this ([Nuget repo](https://dotnet.myget.org/F/uwpcommunitytoolkit/api/v3/index.json) | [Gallery](https://dotnet.myget.org/gallery/uwpcommunitytoolkit)) to your Visual Studio.
