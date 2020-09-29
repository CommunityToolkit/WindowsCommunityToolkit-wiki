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
| **Conditions**   | **Actions**   |
|:------------- |:----------: |
| Is Action | Action: Created |
|Is Activity Sender |User: Author |
|Has Label | Label: needs author feedback :memo:|
|Is Open |

| **Actions**   |
|:----------: |
|Action: Add Label ---> Label: needs attention :wave:|
|Action: Remove Label ---> Label: needs author feedback :memo:|






Needs Triage lablel
| **NuGet Package Name**      | **Description**   |
| :------------- | :----------: |
|  Microsoft.Toolkit | .NET Standard NuGet package containing common code   |

Add Voting to New Feature Request
| **NuGet Package Name**      | **Description**   |
| :------------- | :----------: |
|  Microsoft.Toolkit | .NET Standard NuGet package containing common code   |

Add No Recent Activity label to issues
| **NuGet Package Name**      | **Description**   |
| :------------- | :----------: |
|  Microsoft.Toolkit | .NET Standard NuGet package containing common code   |

Remove no recent label when an issue is commented on
| **NuGet Package Name**      | **Description**   |
| :------------- | :----------: |
|  Microsoft.Toolkit | .NET Standard NuGet package containing common code   |

Issues Needs Attention
| **NuGet Package Name**      | **Description**   |
| :------------- | :----------: |
|  Microsoft.Toolkit | .NET Standard NuGet package containing common code   |

Closing Stale Issues
| **NuGet Package Name**      | **Description**   |
| :------------- | :----------: |
|  Microsoft.Toolkit | .NET Standard NuGet package containing common code   |

Closing Duplicate Issues
| **NuGet Package Name**      | **Description**   |
| :------------- | :----------: |
|  Microsoft.Toolkit | .NET Standard NuGet package containing common code   |

Issues that are closed due to inactivity, reopens an issue if the author posts a reply within 7 days of the closing
| **NuGet Package Name**      | **Description**   |
| :------------- | :----------: |
|  Microsoft.Toolkit | .NET Standard NuGet package containing common code   |

Issues that are closed with no activity for over 7 days, ask non-contributor to consider opening a new issue instead
| **NuGet Package Name**      | **Description**   |
| :------------- | :----------: |
|  Microsoft.Toolkit | .NET Standard NuGet package containing common code   |

Lock closed issues without activity for over 60 days
| **NuGet Package Name**      | **Description**   |
| :------------- | :----------: |
|  Microsoft.Toolkit | .NET Standard NuGet package containing common code   |

Opening Pull Request
| **NuGet Package Name**      | **Description**   |
| :------------- | :----------: |
|  Microsoft.Toolkit | .NET Standard NuGet package containing common code   |

In-PR Label 
| **NuGet Package Name**      | **Description**   |
| :------------- | :----------: |
|  Microsoft.Toolkit | .NET Standard NuGet package containing common code   |


Add Needs Author feedback label When Changes are Requested in PR
| **NuGet Package Name**      | **Description**   |
| :------------- | :----------: |
|  Microsoft.Toolkit | .NET Standard NuGet package containing common code   |

Remove Needs Author Feedback Label when Author Responds
| **NuGet Package Name**      | **Description**   |
| :------------- | :----------: |
|  Microsoft.Toolkit | .NET Standard NuGet package containing common code   |

Remove No Recenet Activity from Pull Reqeuests
| **NuGet Package Name**      | **Description**   |
| :------------- | :----------: |
|  Microsoft.Toolkit | .NET Standard NuGet package containing common code   |


Remove No Recent Activity when PR is commented ON
| **NuGet Package Name**      | **Description**   |
| :------------- | :----------: |
|  Microsoft.Toolkit | .NET Standard NuGet package containing common code   |

Remove No REceent Activity when PR is reviewed
| **NuGet Package Name**      | **Description**   |
| :------------- | :----------: |
|  Microsoft.Toolkit | .NET Standard NuGet package containing common code   |

Close Stale PR
| **NuGet Package Name**      | **Description**   |
| :------------- | :----------: |
|  Microsoft.Toolkit | .NET Standard NuGet package containing common code   |

Add No Recent Activity Label to the PR
| **NuGet Package Name**      | **Description**   |
| :------------- | :----------: |
|  Microsoft.Toolkit | .NET Standard NuGet package containing common code   |


***

If you have any feedback or questions regarding the fabric bot services please reach out to the team via [email](mailto:https://fabricbotservices@microsoft.com) :rocket: 