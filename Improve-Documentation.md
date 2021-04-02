As the community is always working on improving Windows Community Toolkit and introducing new features, we always make certain that our documentation is also updated and meets the requirement of all the current features. Therefore, improving documentation will be a great way to contribute to this project.
 
Currently, all the Windows Community Toolkit Docs are being hosted on [WindowsCommunityToolkitDocs](https://github.com/MicrosoftDocs/WindowsCommunityToolkitDocs) repository and the [Doc PR template](https://github.com/MicrosoftDocs/WindowsCommunityToolkitDocs/blob/master/.github/PULL_REQUEST_TEMPLATE.md) is being followed by the contributors to propose any changes to update the docs for Windows Community Toolkit. 

### How does the Doc process work? 

When opening a Pull Request, start by forking [Windows Community Toolkit Docs](https://github.com/MicrosoftDocs/WindowsCommunityToolkitDocs) repository. Then, based on the type of change you're making you'll need to create a new branch from either the `master` or `dev` branches:

If you have a typo or existing document improvement to an already shipped feature, please base your change off of the [Master branch](https://github.com/MicrosoftDocs/WindowsCommunityToolkitDocs/tree/master). This will allow us to get the change to the published documentation between releases.

For documentation regarding any new features, please base your fork off the last updated dev branch. For example: 'dev/7.1.0'

We will merge updates from the current dev branch to 'master' to keep master in-sync with the live branch. When we make a new release, we will push the live branch in order to publish documentation for new features.

After following the process above, submit the PR, and depending on the improvement you are proposing the changes will eventually appear in these links.

- [[Staging review from 'master' branch](https://review.docs.microsoft.com/en-us/windows/communitytoolkit/?branch=master)] **This link is currently only available for Microsoft Employees**
- [[Live site from 'live' branch](https://docs.microsoft.com/en-us/windows/communitytoolkit/)]
