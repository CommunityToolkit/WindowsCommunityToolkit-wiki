Documentation is required when adding, removing, or updating a control or an API. As the community is always working on improving Windows Community Toolkit and introducing new features, we always make certain that our documentation is also updated and meets the requirement of all the current features.
 
Currently, all the Windows Community Toolkit Docs are being hosted on [WindowsCommunityToolkitDocs](https://github.com/MicrosoftDocs/WindowsCommunityToolkitDocs) repository and the [Doc PR template](https://github.com/MicrosoftDocs/WindowsCommunityToolkitDocs/blob/master/.github/PULL_REQUEST_TEMPLATE.md) is being followed by the contributors to propose any changes to update the docs for Windows Community Toolkit. 

## How does the Doc process work? 

When opening a Pull Request, start by forking [Windows Community Toolkit Docs](https://github.com/MicrosoftDocs/WindowsCommunityToolkitDocs) repository. Then, based on the type of change you're making you'll need to create a new branch from either the `master` or `dev` branches:

### Improve Documentation
If you have a typo or existing document improvement to an already shipped feature, please base your branch off of the [Master branch](https://github.com/MicrosoftDocs/WindowsCommunityToolkitDocs/tree/master). This will allow us to get the change to the published documentation between releases.

### Add Documentation
**Note:** Both Pull Requests (code and docs) must be approved by the core team before either one is merged and make sure to update both Pull Requests with a link to each other.

When adding new documentation page:
* Copy the [documentation template](https://github.com/MicrosoftDocs/WindowsCommunityToolkitDocs/blob/master/docs/.template.md) and follow the same format.
* Update the [Table of Content](https://github.com/MicrosoftDocs/WindowsCommunityToolkitDocs/blob/master/docs/toc.md) to point to the new page.
* Proceed to add the content of new feature and base your fork off the last updated dev branch. For example: 'dev/7.1.0'

We will merge updates from the current main branch to the latest dev branch to keep it in-sync with any updated changes. We will periodically sync the main branch automatically with the live branch to pick up any changes made over time. When we make a new release, we will integrate the dev branch into the main branch in order to publish documentation for new features.

After following the process above, submit the PR, and depending on the improvement you are proposing the changes will eventually appear in these links.

- [[Staging review from 'master' branch](https://review.docs.microsoft.com/en-us/windows/communitytoolkit/?branch=master)] **This link is currently only available for Microsoft Employees**
- [[Live site from 'live' branch](https://docs.microsoft.com/en-us/windows/communitytoolkit/)]

