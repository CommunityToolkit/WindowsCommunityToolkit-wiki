[Fabric Bot Services](https://fabric-cp.azurewebsites.net/bot/) platform is being utilized throughout the Windows Community Toolkit repo to work as an automated bot and perform the tasks on behalf of users to increase productivity and ease the workflow. 

You will see the Bot in action whether you open an Issue, PullRequest, Comment, label, etc

First, you will have to reach out to the team via [email](mailto:https://fabricbotservices@microsoft.com) to request permission to be added in the repo that you are looking to automate. 

Once the request is approved now you are able to customize the repo very easily in different ways. 

Here is how our repo uses the Bot🤖:

Auto-Merge label: This is the label that is used in active Pull Requests to give commands to signoff once all the requirements are met. (In our repo by default 2 reviewers need to sign-off and three checks including Toolkit/CI, WIP, and license/CLI need to be met. The wait time period for the PR is set for 8 hours since the time it was opened. Therefore once the 8 hours are complete and all the requirements are met, the PR will automatically be merged. If the 8 hours are not completed you will see the following message from @msftbot 

"Hello user! Because this pull request has the auto-merge label, I will be glad to assist with helping to merge this pull request once all check-in policies pass.

p.s. you can customize the way I help with merging this pull request, such as holding this pull request until a specific person approves. Simply @mention me (@msftbot) and give me an instruction to get started! Learn more here." 

YOu can customize the auto-merge now by commanding the bot via comments. There are certain scenarios that can be used. 

You can require limits of approval or a specific reviewer to proceed with the PR. 
For example: Merge this Pull request if approved by 3 reviewers or Only merge if "@user" approves the PR. 

You can require approval from a few people to several people. For Example: Only merge the PR if @user1, @user2, and @user3 approve OR Merge the PR if @user1, @user1, or @user1 approves. 

Additionally, you can also hold the PR for a certain time period. For example, Hold the PR for another 8 hours, etc. 
 
You can customize the phrases the way you like and if the bot misinterpreted the phrase you mentioned feel free to say "Nevermind" and it will disregard the last change. 


Replacing Needs Author Feedback label with Needs Attention: The purpose of both of these labels is to improve communication by triggering the labels to involve both the parties to make certain the issue or feature gets resolves in a timely manner. When the Issue or PR is received and the community member has questions they can comment which triggers the author's feedback label which creates visibility for the author to respond. The method can also be applied when the Author comments or response which triggers a Need Attention label for the community members to respond. 
This has been done by setting the following conditions:
The following conditions are used to perform certain tasks
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

**Needs Triage label**
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
<br>

**Add Voting to New Feature Request**
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

**Add No Recent Activity label to issues**
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

**Remove no recent label when an issue is commented on**
| **Conditions**   | **Actions**   |
|:------------- |:----------: |
|**Condition:** Has Label | Label: no-recent-activity :chart_with_downwards_trend:|

<br>

| **Actions**   | **Triggers**   |
|:---------- |:---------- |
|**Action:** Remove Label | **Label:** no-recent-activity :chart_with_downwards_trend:|

<br><br>


**Issues Needs Attention**
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


**Closing Stale Issues**

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


**Closing Duplicate Issues**

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

**Issues that are closed due to inactivity, reopens an issue if the author posts a reply within 7 days of the closing**

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
<br>

**Issues that are closed with no activity for over 7 days, ask non-contributor to consider opening a new issue instead**
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


**Lock closed issues without activity for over 60 days**
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


**Opening Pull Request**
| **Conditions**   | **Actions**   |
|:------------- |:----------: |
| **Condition:** Is Action | **Action:** Opened |

| **Actions**   | **Triggers**   |
|:----------: |:---------- |
|**Action:** Add Reply | **Reply:** Thanks ${issueAuthor} for opening a Pull Request! The reviewers will test the PR and highlight if there is any conflict or changes required. If the PR is approved we will proceed to merge the pull request :raised_hands:|
|**Action:** Request Reviewer | **Reviewer:** @user|

<br><br>

**In-PR Label**
| **Conditions**   | **Actions**   |
|:------------- |:----------: |
| **'In-PR' label:** Label |
| **Enable 'Fixed' Label?** 'Fixed' Label: Label |

<br><br>


**Add Needs Author feedback label to PR When Changes are Requested**
| **Conditions**   | **Actions**   |
|:------------- |:----------: |
| **Condition:** Is Action | **Action:** Submitted |
| **Condition:** Is review state |**State:** Changed requested |
<br>

| **Actions**   | **Triggers**   |
|:----------: |:----------: |
|**Action:** Add Label | **Label:** needs author feedback :memo:|

<br><br>


**Remove Needs Author Feedback Label when Author Responds**
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

**Remove No Recenet Activity from Pull Reqeuests**
| **Conditions**   | **Actions**   |
|:------------- |:----------: |
| **Condition:** Is Action | **Action:** Closed |
| **Condition:** Has Label |**Label:** no-recent-activity :chart_with_downwards_trend: |
<br>

| **Actions**   | **Triggers**   |
|:---------- |:----------
|**Action:** Remove Label | **Label:** no-recent-activity :chart_with_downwards_trend:|

<br><br>

Event responder Pull Request Comments
**Remove No Recent Activity when PR is commented ON**
| **Conditions**   | **Actions**   |
|:------------- |:----------: |
| **Condition:** Has Label |**Label:** no-recent-activity :chart_with_downwards_trend: |
<br>

| **Actions**   | **Triggers**   |
|:---------- |:----------
|**Action:** Remove Label | **Label:** no-recent-activity :chart_with_downwards_trend:|

<br><br>

Event responder - pull request reviews
**Remove No Recent Activity when PR is reviewed**
| **Conditions**   | **Actions**   |
|:------------- |:----------: |
| **Condition:** Has Label |**Label:** no-recent-activity :chart_with_downwards_trend: |
<br>

| **Actions**   | **Triggers**   |
|:---------- |:----------
|**Action:** Remove Label | **Label:** no-recent-activity :chart_with_downwards_trend:|

<br><br>

Scheduled search
**Close Stale PR**
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

**Add No Recent Activity Label to the PR**
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

***

If you have any feedback or questions regarding the fabric bot services please reach out to the team via [email](mailto:https://fabricbotservices@microsoft.com) :rocket: 