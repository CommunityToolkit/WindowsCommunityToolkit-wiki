[Fabric Bot Services](https://fabric-cp.azurewebsites.net/bot/) platform is being utilized in the Windows Community Toolkit repository as an automation tool to ease the workflow and improve productivity.  

You will see the Bot in action whether you plan to open an Issue, Submit a Pull Request, Make a Comment, label the PR's or issues, etc

To activate the bot you will have to reach out to the team via [email](mailto:https://fabricbotservices@microsoft.com) regarding the permission to be added in the repo that you are looking to automate.

Once the request is approved, then you will be able to go to the list of selected repositories in Fabric Bot and customize the tasks that need to be performed by applying certain conditions and actions. All the conditions are customizable and can be adjusted based on the need or task you want to perform. 

**Below are the tasks that the WCT team currently uses to automate the issues in the repository** :robot:

### Needs Triage label

Needs Triage is the most used label which can be observed in all the issues of the repo. As the name suggests it is used to triage the issues, features, or any request whenever first opened in the WCT. The purpose of the label is to create visibility and ensure the author that the issue has been received and will be triaged to the appropriate team to ensure faster response and possible resolution. The following conditions and actions are used in the Fabric Bot portal to apply the label and a welcome message by @msftbot.

**Event responder - issues**

| **Conditions**   | **Actions**   |
|:------------- |:----------: |
| **Condition:** Is Action | **Action:** Opened |
| **Condition:** <ul><li>- [x] Not: Is part of any project</li></ul> |
| **Condition:**  <ul><li>- [x] Not: Is assigned to someone</li></ul> |
|**Condition:** Has Label | **Label:** bug :bug:|
<br>

| **Actions**   | **Triggers**|
|:----------: |:---------- |
|**Action:** Add Label | **Label:** needs triage :mag:|
|**Action:** Add Reply | **Label:** I have automatically added a "needs triage" label to help get things started. Our team will analyze and investigate the issue, and escalate it to the relevant team if possible. Other community members may also look into the issue and provide feedback :raised_hands:|

<br><br>

### Replace needs author feedback label with needs attention label when the author comments on an issue

The purpose of the following label is to ensure the continued momentum of the issue and to be certain there are no delays in responses from the party that is helping solve the problem. Therefore when the Author will comment on the issue @msftbot bot will automatically apply the "needs attention :wave:" label to alert other parties to respond back to the author and expedite the issue. 

**Event responder - issue comments**


| **Conditions**   | **Actions**   |
|:------------- |:----------: |
|**Condition:** Is Action | **Action:** Created |
|**Condition:** Is Activity Sender |**User:** Author |
|**Condition:** Has Label | **Label:** needs author feedback :memo:|
|**Condition:** Is Open |
<br>

Actions of the conditions applied above. 
| **Actions**   | **Triggers** |
|:---------- |:----------: |
|**Action**: Add Label | **Label**: needs attention :wave:|
|**Action**: Remove Label | **Label**: needs author feedback :memo:|

<br><br>

### Add Voting to a New Feature Request

When the author will first open the feature request to introduce an idea or suggestions that can either improve the performance or innovate WCT, it will be responded back with the message by the bot that will greet and Add the Thumbs as a voting feature. Then the rest of the community will checkout the feature whether it's worth implementing in WCT or not. If they like the feature they will add more thumps up on top of the existing one to ensure the feature request must be adopted. 

**Event responder - issues**

| **Conditions**   | **Actions**   |
|:------------- |:----------: |
| **Condition:** Is action | **Action**: Opened |
| **Condition:** <ul><li>- [x] Not: Is part of any project</li></ul> |
| **Condition:** <ul> <li>- [x] Not: Is assigned to someone</li></ul> |
| **Condition:** Has Label | **Label**: feature request :mailbox:|
<br>

| **Actions**   |    **Actions**   |
|:---------- | :---------- |
|**Action:** Add Reaction | Reaction: :+1:|
|**Action:** Add reply | **Reply:** Hello, '${issueAuthor}! Thanks for submitting a new feature request. I've automatically added a vote :+1: reaction to help get things started. Other community members can vote to help us prioritize this feature in the future!|

<br><br>

### Add No Recent Activity label to issues

"No Recent Activity" label will ensure and alert the author with labels and messages that they have not responded to or performed any activity for 15 days. It will also provide warnings that the issue will be closed if it continued to be untouched or left without activity. The label provides greater visibility and triggers to make certain there are no delays.

**Scheduled search**

| **Conditions**   | **Actions**   |
|:------------- |:----------: |
| **Frequency:** <ul><li>- [x] Every 3 hours, 8 times a day</li></ul> |
| **Search term:** Is issue |
| **Search term:** Is open|
| **Search term:** Has Label | **Label:** needs author feedback :memo:|
| **Search term:** No activity since |**Days since last activity:** 15 |
| **Search term:** Does not have label | **Label:** no-recent-activity :chart_with_downwards_trend:|
<br>

| **Actions**   |  **Triggers**   |
|:----------: |:---------- |
|**Action:** Add Label | **Label:** no-recent-activity :chart_with_downwards_trend:|
|**Action:** Add Reply | **Reply:** This issue has been automatically marked as stale because it has been marked as requiring author feedback but has not had any activity for **15 days**. It will be closed if no further activity occurs **within 30 days of this comment**.|

<br><br>

### Remove no recent label when an issue is commented on

Once the comment has been made in the issue the "no-recent-activity :chart_with_downwards_trend:" will be removed. This ensures that the productivity of the issue will continue and proceeds towards a possible solutions to the problem.

**Event responder - issue comments**

| **Conditions**   | **Actions**   |
|:------------- |:----------: |
|**Condition:** Has Label | Label: no-recent-activity :chart_with_downwards_trend:|

<br>

| **Actions**   | **Triggers**   |
|:---------- |:---------- |
|**Action:** Remove Label | **Label:** no-recent-activity :chart_with_downwards_trend:|

<br><br>

### Issues Needs Attention

"needs attention :wave:" label with the message will be triggered to alert all the stakeholders that are involved in certain issues. This ensures transparency that the issue has been sitting without any activity for 15 days. Therefore it is essential to establish procedures that will either provide further guidance or triage the issue to the appropriate team that can resolve the issue in a timely manner. 

**Scheduled search**

| **Conditions**   | **Actions**   |
|:------------- |:----------: |
| **Frequency:** <ul><li>- [x] Every 3 hours, 8 times a day</li></ul> |
| **Search term:** Is issue |
| **Search term:** Is open|
| **Search term:** Has Label | **Label:** needs triage :mag:|
| **Search term:** No activity since |**Days since last activity:** 15 |
<br>

| **Actions**   |  **Triggers**   |
|:----------: |:---------- |
|**Action:** Add Label | **Label:** needs attention :wave:|
|**Action:** Add Reply | **Reply:** This issue has been marked as "needs attention :wave:" due to no activity for **15 days**.  Please triage the issue so the fix can be established. |
<br><br>

### Closing Stale Issues

At this point after many alerts to the issue that required author feedback if still hasn't been responded @msftbot will the run the search based on these conditions and if any such issues are filtered it will respond the messaged regarding failure to respond to the issue and will automatically close the issue. Such actions are used to better manage the issue and to ensure the issues are just left open aren't cluttered in the repo and blocks the focus on issues that are active. 

**Scheduled search**

| **Conditions**   | **Actions**   |
|:------------- |:----------: |
| **Frequency:** <ul><li>- [x] Every 3 hours, 8 times a day</li></ul> |
| **Search term:** Is issue |
| **Search term:** Is open|
| **Search term:** Has Label | **Label:** needs author feedback :memo:|
| **Search term:** Has Label | **Label:** no-recent-activity :chart_with_downwards_trend:|
| **Search term:** No activity since |**Days since last activity:** 60 |
<br>

| **Actions**   |  **Triggers**   |
|:----------: |:---------- |
|**Action:** Add Reply | **Reply:** This issue has been automatically closed because it was marked as requiring author feedback but has not had any activity for over **60 days**. |
|**Action:** Close |

<br><br>

### Closing Duplicate Issues

The conditions of this action runs regularly to ensure if there is an issue open with the Duplicate label, then @msftbot can respond to the issue with the message that the issue was open for 1 day and will be closed due to the fact it is a duplicate issue. 

**Scheduled search**

| **Conditions**   | **Actions**   |
|:------------- |:----------: |
| **Frequency:** <ul><li>- [x] Every 3 hours, 8 times a day</li></ul> |
| **Search term:** Is issue |
| **Search term:** Is open|
| **Search term:** Has Label | **Label:** duplicate :busts_in_silhouette:|
| **Search term:** No activity since |**Days since last activity:** 1 |
<br>

| **Actions**   |  **Triggers**   |
|:----------: |:---------- |
|**Action:** Add Reply | **Reply:** This issue has been marked as duplicate and has not had any activity for **1 day**. It will be closed for housekeeping purposes. |
|**Action:** Close |

<br><br>

### Issues that are closed due to inactivity, reopens an issue if the author posts a reply within 7 days of the closing

If an author responds to the issues that were closed earlier due to lack of participation or inactivity @msfbot will run the following conditions and see if it was within 7 days and if it fulfills all the requirement @msftbot will automatically reopen the issue and add the needs attention label to ascertain to provide a fresh start and possible resolution of the issue with the help of deleting any label such as no-recent-activity :chart_with_downwards_trend: and needs author feedback :memo: to ensure issue looks clean and will be solved. 

**Event responder - issue comments**

| **Conditions**   | **Actions**   |
|:------------- |:----------: |
| **Condition:** <ul><li>- [x] Not Is open</li></ul> |
| **Condition:** Is action | **Action**: Created|
| **Condition:** Has label | **Label**: needs author feedback :memo:|
| **Condition:** Has label | **Label**: no-recent-activity :chart_with_downwards_trend:|
| **Condition:** <ul> <li>- [x] Not: No activity since... </li></ul> | **Days ago**: 7|
| **Condition:** <ul> <li>- [x] Not: Is 'close and comment' action</li></ul> |
| **Condition:** Is activity sender | **User**: Author|
| **Condition:** <ul> <li>- [x] Not: Activity sender has permissions</li></ul> | **Permissions**: None|
<br>

| **Actions**   |  **Triggers**   |
|:----------: |:---------- |
|**Action:** Reopen issue |
|**Action:** Remove label | **Label:** no-recent-activity :chart_with_downwards_trend: |
|**Action:** Remove label | **Label:** needs author feedback :memo: |
|**Action:** Add label | **Label:** needs attention :wave: |
<br><br>

### Issues that are closed with no activity for over 7 days, ask the non-contributor to consider opening a new issue instead

The issues that were closed for over 7 days and then a non-contributor attempt to open the issues then the following condition will be applied to make certain that the issue does not re-open. When the non-contributor will comment on this closed issue @msftbot will respond to the non-contributor that they will have to open a new issue instead. Such action is to make certain that not everyone can open the closed issue since it could be closed for many reasons. The action is used to reduced unwanted issues to be open. 

**Event responder - issue comments**

| **Conditions**   | **Actions**   |
|:------------- |:----------: |
| **Condition:** Is Action | **Action:** Created |
| <ul> <li>- [x] Not: Is Open </li></ul> |
| **Condition:** Activity Sender has permissions | **Permissions:** None |
| **Condition:** No activity Since | **Days ago:** 7|
| **Condition:** <ul> <li>- [x] Not: Is 'close and comment' action</li></ul>|

| **Actions**   |
|:----------: |
|**Action:** Add reply | **Reply:** Hello lovely human, thank you for your comment on this issue. Because this issue has been closed for a period of time, please strongly consider opening a new issue linking to this issue instead to ensure better visibility of your comment. Thank you!|

<br><br>

### Lock closed issues without activity for over 60 days

The action of this task is self-explanatory that any issues that will be closed for over 60 days will automatically be locked. This will ensure that no further activity is done in the closed issue since 60 days is used as a grace period where incase if any stakeholder still wants to comment or have questions. The conditions are performed by @msftbot every three hours to better manage the issues that are closed and keep the repository clean and well managed.  

**Scheduled search**

| **Conditions**   | **Actions**   |
|:------------- |:----------: |
| **Frequency:** <ul><li>- [x] Every 3 hours, 8 times a day</li></ul> |
| **Search term:** Is closed |
|**Search term:** No activity since | **Days since last activity:** 60|
|**Search term:** Is unlocked|
|**Search term:** Is issue|

<br>

| **Actions**   | **Triggers**   |
|:------------- |:----------: |
|**Action:** Add Label | **Reason:** Resolved|

<br><br>

**Below are the tasks that the WCT team currently uses to automate the PR's in the repository** :robot:


### Opening Pull Request

When a contributor opens a Pull Request in WCT repository @msftbot runs the following conditions to ensure that its a very clean and transparent process for the author. Therefore when the PR is opened @microsoft will add the greetings message by automatically detecting the author's name via ${issueAuthor} which is another great feature of the bot service. This acknowledges and recognizes the author for their contribution and tags the selective members of the WCT team to who will perform the testing for the author. The purpose of this procedure is to ensure that the author feels welcomed and the WCT appreciates the time of the author therefore expediting the process faster to merge in the repo. 

**Event responder - pull requests**

| **Conditions**   | **Actions**   |
|:------------- |:----------: |
| **Condition:** Is Action | **Action:** Opened |

| **Actions**   | **Triggers**   |
|:----------: |:---------- |
|**Action:** Add Reply | **Reply:** Thanks ${issueAuthor} for opening a Pull Request! The reviewers will test the PR and highlight if there is any conflict or changes required. If the PR is approved we will proceed to merge the pull request :raised_hands:|
|**Action:** Request Reviewer | **Reviewer:** @user|

<br><br>

### In-PR Label

This feature is used as an indicator of the issue that there is a PR open in the repository which will be merged to solve this issue. This is completed when the author opens a PR and includes the issue number in the PR template as #Fixes 1234 (1234 is used an issue number for demo purposes). Once these steps are performed @msftbot will automatically detect the issue mentioned in the PR and tag as "In-PR :rocket:" label to alert the author of the issue or stakeholders for transparency and visibility.


| **Conditions**   | **Actions**   |
|:------------- |:----------: |
| **'In-PR' label:** Label |
| **Enable 'Fixed' Label?** 'Fixed' Label: Label |

<br><br>

### Add Needs Author feedback label to PR When Changes are Requested

When the author opens the PR, and the stakeholders respond to the PR seeking the author's response the bot will run the following condition and apply the needs author feedback :memo: label in the PR. This is to alert the Author that the activity has occurred and they need to respond so the merge can be applied faster. The purpose of the task is to improve productivity and to provide possible resolution. 
 
**Event responder - pull request reviews**

| **Conditions**   | **Actions**   |
|:------------- |:----------: |
| **Condition:** Is Action | **Action:** Submitted |
| **Condition:** Is review state |**State:** Changed requested |
<br>

| **Actions**   | **Triggers**   |
|:----------: |:----------: |
|**Action:** Add Label | **Label:** needs author feedback :memo:|

<br><br>


### Remove Needs Author Feedback Label when Author Responds

The purpose of the following label is to ensure the continued momentum of the PR and to be certain there are no delays in responses from the party that is helping solve the problem. Therefore when the Author comments or perform any activity on the issue @msftbot bot will automatically remove needs author feedback :memo: label and apply the "needs attention :wave:" label to alert other parties to respond back to the author and expedite the PR.

**Event responder - pull requests**

| **Conditions**   | **Actions**   |
|:------------- |:----------: |
| **Condition:** Is activity sender| **User:** Author |
| **Condition:** <ul><li>- [x] Not: Is action</li></ul> | **Is action:** Closed|
|**Condition:** Has Label | **Label:** needs author feedback :memo:|
<br>

| **Actions**   | **Triggers**   |
|:---------- |:---------- |
|**Action:** Remove Label | **Label:** needs author feedback :memo:|
|**Action:** Add Label | **Label:** needs attention :wave:|
|**Action:** Add Reply | **Reply:** This PR has been marked as "needs attention :wave:" and awaiting a response from the team. |

<br><br>

### Remove No Recent Activity when PR is commented ON

Once the comment has been made in the PR the "no-recent-activity :chart_with_downwards_trend:" will be removed. This ensures that the productivity of the PR will continue and proceeds towards possible solutions to the problem.

**Event responder Pull Request Comments**

| **Conditions**   | **Actions**   |
|:------------- |:----------: |
| **Condition:** Has Label |**Label:** no-recent-activity :chart_with_downwards_trend: |
<br>

| **Actions**   | **Triggers**   |
|:---------- |:----------
|**Action:** Remove Label | **Label:** no-recent-activity :chart_with_downwards_trend:|

<br><br>

### Remove No Recent Activity when PR is reviewed

Once the PR is reviewed the "no-recent-activity :chart_with_downwards_trend:" will be removed. This ensures that the productivity of the PR will continue and proceeds towards possible solutions to the problem.

**Event responder - pull request reviews**


| **Conditions**   | **Actions**   |
|:------------- |:----------: |
| **Condition:** Has Label |**Label:** no-recent-activity :chart_with_downwards_trend: |
<br>

| **Actions**   | **Triggers**   |
|:---------- |:----------
|**Action:** Remove Label | **Label:** no-recent-activity :chart_with_downwards_trend:|

<br><br>

### Close Stale PR

At this point after many alerts to the PR that required author feedback if still hasn't been responded @msftbot will the run the search based on the following conditions and if any such issues are filtered it will respond the messaged regarding failure to respond to the issue and will automatically close the PR. Such actions are used to better manage the PR and to ensure that the PR's are just left open isn't cluttered in the repo and blocks the focus on PR's that are active. 

**Scheduled search**

| **Conditions**   | **Actions**   |
|:------------- |:----------: |
| **Frequency:** <ul><li>- [x] Every 3 hours, 8 times a day</li></ul> |
| **Search term:** Is pull request |
|**Search term:** Is open|
|**Search term:** Has Label | **Label:** needs author feedback :memo:|
|**Search term:** Has Label | **Label:** no-recent-activity :chart_with_downwards_trend:|
|**Search term:** No activity since |**Days since last activity:** 45 |
 <br>
 
| **Actions**   | **Triggers**   |
|:----------: |:----------|
|**Action:** Close|

<br><br>

### Add No Recent Activity Label to the PR

"No Recent Activity" label will ensure and alert the author with labels and messages that they have not responded to or performed any activity for 15 days. It will also provide warnings that the PR will be closed if it continued to be untouched or left without activity or comments. The label provides greater visibility and triggers to make certain there are no delays. 

**Scheduled search**

| **Conditions**   | **Actions**   |
|:------------- |:----------: |
| **Frequency:** <ul><li>- [x] Every 3 hours, 8 times a day</li></ul> |
| **Search term:** Is pull request |
|**Search term:** Is open|
|**Search term:** Has Label | **Label:** needs author feedback :memo:|
|**Search term:** No activity since |**Days since last activity:** 15 |
|**Search term:** Does not have label | **Label:** no-recent-activity :chart_with_downwards_trend:|
 <br>
 
| **Actions**   | **Triggers**   |
|:----------: |:----------|
|**Action:** Add Label | **Label:** no-recent-activity :chart_with_downwards_trend:|
|**Action:** Add Reply | **Reply:** This pull request has been automatically marked as stale because it has been marked as requiring author feedback but has not had any activity for **15 days**. It will be closed if no further activity occurs **within 30 days of this comment**.|

<br><br>


### Auto-merge pull requests

* Auto-merge label: auto merge
* Minimum time in minutes pull request must be open before being auto-merged: 480
* Merge Strategy: Merge
<ul><li>- [x] Auto delete branches when possible after merge?</li></ul> 
<ul><li>- [x] Remove auto-merge label when someone without write access pushes changes?</li></ul>

This is the label that is used in active Pull Requests to give commands to signoff once all the requirements are met. (In our repo by default 2 reviewers need to sign-off and three checks including Toolkit/CI, WIP, and license/CLI need to be met. The wait time period for the PR is set for 8 hours since the time it was opened. Therefore once the 8 hours are complete and all the requirements are met, the PR will automatically be merged. If the 8 hours are not completed you will see the following message from @msftbot 

"Hello user! Because this pull request has the auto-merge label, I will be glad to assist with helping to merge this pull request once all check-in policies pass.

p.s. you can customize the way I help with merging this pull request, such as holding this pull request until a specific person approves. Simply @mention me (@msftbot) and give me an instruction to get started! Learn more here." 

YOu can customize the auto-merge now by commanding the bot via comments. There are certain scenarios that can be used. 

You can require limits of approval or a specific reviewer to proceed with the PR. 
For example: Merge this Pull request if approved by 3 reviewers or Only merge if "@user" approves the PR. 

You can require approval from a few people to several people. For Example: Only merge the PR if @user1, @user2, and @user3 approve OR Merge the PR if @user1, @user1, or @user1 approves. 

Additionally, you can also hold the PR for a certain time period. For example, Hold the PR for another 8 hours, etc. 
 
You can customize the phrases the way you like and if the bot misinterpreted the phrase you mentioned feel free to say "Nevermind" and it will disregard the last change. 


Replacing Needs Author Feedback label with Needs Attention: The purpose of both of these labels is to improve communication by triggering the labels to involve both the parties to make certain the issue or feature gets resolves in a timely manner. When the Issue or PR is received and the community member has questions they can comment which triggers the author's feedback label which creates visibility for the author to respond. The method can also be applied when the Author comments or response which triggers a Need Attention label for the community members to respond. 

***

If you have any feedback or questions regarding the fabric bot services please reach out to the team via [email](mailto:https://fabricbotservices@microsoft.com) :rocket: 