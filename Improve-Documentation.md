As the community is always working on improving Windows Community Toolkit and introducing new features, we always make certain that our documentation is also updated and meets the requirement of all the current features. Therefore, improving documentation will be a great way to contribute to this project.
 
Currently, all the Windows Community Toolkit Docs are being hosted on [WindowsCommunityToolkitDocs](https://github.com/MicrosoftDocs/WindowsCommunityToolkitDocs) repository and the [Doc PR template](https://github.com/MicrosoftDocs/WindowsCommunityToolkitDocs/blob/master/.github/PULL_REQUEST_TEMPLATE.md) is being followed by the contributors to propose any changes to update the docs for Windows Community Toolkit. 

### How does the Doc process work? 

When opening a Pull Request, start by forking this repository. Then, based on the type of change you're making you'll need to create a new branch from either the `master` or `live` branches:

For documentation for new features, please base your fork off the master branch.

If you have a typo or existing document improvement to an already shipped feature, please base your change off of the [live branch](https://github.com/MicrosoftDocs/WindowsCommunityToolkitDocs/tree/live). This will allow us to get the change to the published documentation between releases.

We will periodically merge updates from the live branch to master to keep master in-sync with the published docs. When we make a new release, we will push master to the live branch in order to publish documentation for new features.

After following the process above, submit the PR, and depending on the improvement you are proposing the changes will eventually appear in these links.

- [[Staging review from 'master' branch](https://review.docs.microsoft.com/en-us/windows/communitytoolkit/?branch=master)] **This link is currently only available for Microsoft Employees**
- [[Live site from 'live' branch](https://docs.microsoft.com/en-us/windows/communitytoolkit/)]

