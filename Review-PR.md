Reviewing PR’s is essential before merging any changes regarding bug fixes, features, doc improvements etc. You can find the current list of PR’s [here](https://github.com/windows-toolkit/WindowsCommunityToolkit/pulls).

🌙 Each PR will also build [[Preview Packages]], so if you're familiar with NuGet and already using the Toolkit, you can easily try new features with these builds. Otherwise, to build a PR yourself, follow the steps below.
 
**Pre-requisites:** Download [Visual Studio](https://visualstudio.microsoft.com/vs/) 2017 or 2019, Install [Windows Community Toolkit Sample App](https://www.microsoft.com/en-us/p/windows-community-toolkit-sample-app/9nblggh4tlcq?rtc=1&activetab=pivot:overviewtab), [Install Git](https://github.com/github/hub#installation), [Install Hub](https://hub.github.com/#install)

Steps to review PR
* Open Command Prompt or [Windows Terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701?activetab=pivot:overviewtab)
* Locate the place where you want the WCT clone to appear by using the cd path. 
* Go to [Windows Community Toolkit](https://github.com/windows-toolkit/WindowsCommunityToolkit) repository and click on **Code** button to copy the HTTPS or SSH URL.
* Paste the link in Command Prompt by following the [Hub Command](https://hub.github.com/#developer) to Clone Windows Community Toolkit.
* [Fork](https://hub.github.com/#contributor) the repo by following the command.
* Checkout PR by using [hub pr checkout](https://hub.github.com/hub-pr.1.html#synopsis) Command
* Open the Visual Studio 
* Click on “Open a project or solution” 
* Locate the cloned repository folder in the local machine and select .sln file to open the solution.
* You will see the PR checkout branch in the bottom right corner of the Visual Studio page. (By default it should have been on the master branch but since the PR checkout command has been performed; therefore, it’s on the branch that is ready to be tested).
* Now run the Microsoft.Toolkit.Uwp.SampleApp and Open [Windows Community Toolkit Sample App](https://www.microsoft.com/en-us/p/windows-community-toolkit-sample-app/9nblggh4tlcq?rtc=1) as well. 
* Review and test the changes side by side.
* Once approved signoff by leaving feedback and results. 

:bulb:	List of [Hub Commands](https://hub.github.com/hub.1.html#commands) that can be useful to manage Pull Request. 

Overall, it is essential to make sure the PR is on the feature branch of the forked repository it does not contradict with any other changes. If it has multiple changes then make certain it is clearly stated in the [PR Template](https://github.com/windows-toolkit/WindowsCommunityToolkit/blob/master/.github/PULL_REQUEST_TEMPLATE.md) with the detailed information and all the requirements of the PR checklist have been fulfilled.

It is also significant to watch if the PR contains any breaking changes or not. If the PR contains a breaking change, check for the detailed description of the impact and migration path for the existing application.

:rotating_light: Breaking changes are likely to be rejected within minor release cycles or held until major versions. 
