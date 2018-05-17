# Engineering Manager Guide to Post Mortem

[Powerpoint Deep Dive](https://microsoft.sharepoint.com/teams/skypespacesteamnew/_layouts/15/WopiFrame2.aspx?sourcedoc=%7B91b1f717-d35c-4559-a47a-b893aab44885%7D&action=edit)

# Meet compliance obligations

**To meet compliance, we need to have a great record of incidents, root cause, actions taken and prevention. The guidelines below help our team with consistency and to meet our obligations in terms of auditing. There is a great set of guiding questions in the below O365 SOP that we have included for reference. It is important that folks avoid assessing and focus on bring the facts to life. We want our audit trail to be accurate and cover as much of the incident as possible**

[From section 4.4.2 (OFFICE 365 SECURITY SERVICES, SECURITY INCIDENT RESPONSE, STANDARD OPERATING PROCEDURES)](https://microsoft.sharepoint.com/teams/o365sec/sir/Standard%20Operating%20Procedures/Forms/AllItems.aspx?viewpath=%2Fteams%2Fo365sec%2Fsir%2FStandard%20Operating%20Procedures%2FForms%2FAllItems%2Easpx&id=%2Fteams%2Fo365sec%2Fsir%2FStandard%20Operating%20Procedures%2FO365%20Security%20Response%20SOP%20v1%2E8%20FINAL%2Edocx&parent=%2Fteams%2Fo365sec%2Fsir%2FStandard%20Operating%20Procedures)

# Incident Ownership

**[ ] Severity must correctly expressing service/user impact.**

```
Some common rule of thumbs:
- PII requires security audit to gauge Severity
- 100% outage for any given platform regardless of volume is at least sev 2
- 100% outage for any region regardless of volume is at least sev 2
- Dialtone must be a minimum sev 2
- Core can start at sev 3    
- Sev 1 usually indicate catastrophic incident or incident involving multiple teams (AAD, Graph)
```
Examples:
- `Good` Users can not renew auth tokens to AAD (Severity 1) 
- `Good` 5% of Users can not make phone calls in Europe (Severity 2)
- `Good` 12% of Users can not make phone calls (Severity 1)
- `Bad` 25% of Users can not see their profile picture (Severity 1) 
    - *this is an optimal scenario and never reaches sev 1*
- `Bad` 500 tenants could not make calls (Severity 3)
    - *this a dialtone scenario so this should clearly be sev 2 at least and more if the number of tenants is significant*


**[ ] Title must correctly describe the user impact / service impact.**
```
Some common rules:
- Title should not contain the root cause
- Title should not express the monitor title
- Title should not contain marker names
- Title can contain region info
- Title can contain relevant services (MSA vs AAD)
- Title should express user experience (Not receiving push notifications)
```
Examples:
- `Good` Users cannot renew auth tokens to AAD
- `Good` 5% of Users cannot make phone calls in EMEA
- `Bad` PII data being logged by web client 
    - *This is too vague. This doesn't indicate what type of data was logged, where it was logged or which area of the webclient*
- `Bad` GetFiles Teamcontroller scenario availability dropped to 56% by a single session. 
    - *This is too technical and doesn't indicate user impact. Avoid api names and don't describe internal symptoms should focus on user experience."*
- `Bad` get-SsoAdalToken-send scenario marker needs tuning
    - *This indicates a scenario marker and makes people guess what was wrong. It does not explain why this is a livesite."*
- `Bad` Exceptions in Firehose processing
    - *Again internal symptoms and no executive level can understand the user impact.*


**[ ] Owning service should be as specific feature area**
Examples:
- `Good` Messaging
- `Good` Calling
- `Bad` TACO 
   - *This is an acronym and no one will understand.*
- `Teams`
   - *This is generic and ambiguious.*

**[ ] Owner field must be a GEM (General Engineering Manager) even if you are not presenting.**
Examples: 
- `Good` *Dan Massey, Alok Sinha*

**[ ] Incident manager and Communications manager are not required**

**[ ] TTD **
```
Guidelines:
- Should never be 0m
- TTD should be the time for the incident to be detected or monitor had fired.
- Note that a monitor ticket you should look into the look bad time to see when the actual start time is.
```

**[ ] TTE**
```
Guidelines:
- Should only be the last mitigating engineer
- This can be 0m if the acknowledging on-call was also the mitigating engineer (ie. SRE)
- This is not purely the first person to acknowledge the incident because they might not do the mitigation.
- If the team responsible is outside of our org, it would be when the engineer on the final partner team that mitigated 
- This could be tracked via email or text as well so be aware of that.
```

**[ ] TTM**
```
Guidelines:
- Should never be 0m (diff)
- Should be the time when the user symptoms are mitigated
- We will track multiple mitigations in the mitigation description below (TTM) here tracks how fast we are able to respond after engagement
```

**[ ] TTN is optional, since we don't use Azure comms manager**

# Timeline

**[ ] Impact start should be the introduction of this breaking change to PROD, comment should contain reasoning**
```
Guidelines:
- It could be when the commit reached prod (deployment)
- If not possible we can use the commit date of the PR
- If not possible we can use the commit date
- Service impact could be when the first failure events start occuring (from dashboard data)
```
Examples:
- `Good` March 14, 2017 10:00:00 AM
    - *Initial GA launch date is a better start date than the commit check in date because it is when the issue was in PROD*
- `Good` Datetime of pool swap for MT
    - *This is a good time because regardless of the AFD switch time, this is a good estimate of impact start*
- `OK` Datetime of a commit check in to develop
    - *This is ok if you don't know the release time, but there can be a significant delay from check in to prod impact.*
    - *This is Good if this was a config change that impacts PROD immediately like feature flag PR*
- `OK` Datetime of the first bad events from the graphs or monitors
    - *This is ok, because it might be an infrastructure (DNS, load balancer) issue.*
    - *This is bad if this was caused by a code change, but the issue did not exhibit until later. In that case the start time would be when the change went to PROD.*
- `BAD` Datetime of the ticket creation
    - *This is never the real start datetime. This is most likely your detection datetime.*
    - *If you only have the monitor to go by you should find out the lookback time and subtract that from the ticket creation time.*

**[ ] Detection should be when the issue was detected, comment should contain the source of the detection**
```
Guidelines:
- Monitors are easy source of this information
- Human detection should be when the first emails were sent out to notify the team
- Human detection could be when the first text over sfb or channel post
- Detection could also be when the partner team detected it (not when they escalated to us)
```
Examples:
- `Good` The time when the first ICM ticket was created
- `Good` The time when the CSS ticket is transferred into ICM
- `Bad` The time when the ranger's ticket was moved into the Tier 1 bucket
   - *This isn't true, the customer detected this and told us so that is the truer date.*
- `OK` The time of an email first reporting the issue
   - *This is only ok if no monitor detected a service issue*

**[ ] Eng. Engaged should be when the actionable engineer was engaged, comment should list this team or person**
```
Guidelines:
- It is not often the SRE or on-call
- It is the development engineer that can pinpoint the mitigation
- It can be the first engineer to respond from Tier 2
- It is not when someone acknowledges the incident
- It is not when triaging and/or searching for a responsible party
```
Examples:
- `Good` The datetime when the SRE triggered a failover
   - *This is a good time if the failover can take a few minutes.*
- `Bad` The datetime of the SRE triggering a machine recycle, but was actually mitigated by hotfix.
   - *In this case the hotfix was the real mitigation but it was wrong to use the machine recycle as the mitigation time.*
- `Good` The date time of shutting down scenario test machines, even though a hotfix was needed to fully fix the issue.
   - *In this case the machine shut down restored traffic health, so it was the true mitigation. The hotfix was relevant to the recovery.*

**[ ] Mitigation is when user symptoms are back at SLA, comment should list what that action was**
```
Guidelines:
- It is not the first mitigation, it's the mitigation that removes the user impact symptoms
```
Examples:
- `Good` The time that the failover stopped bad events from occurring.
- `Bad` The time that the failover was started.
   - *This might not be a good time because a failover could take half an hour or an hour later.*
- `Good` The time when known issues list was updated with the issue.
   - *Some issues can't be resolved quickly so customer notification is the only solution. So the datetime of the customer email is sufficient*
- `Bad` The time when a hotfix was deployed, even though symptoms were mitigated by shutting down scenario tests.
   - *The mitigation was actually the machine shutdown and the time when the symptoms stopped is the correct time.**

**[ ] Recovery should be when the whole incident is taken care of.**
```
Guidelines:
- It is after all mitigations have taken hold
- It is after any data recovery is done
- It is when all PII has been removed.
```
Examples:
- `Good` Datetime service impact was fully restored by mitigation
   - *This is a simple case of impact mitigation*
- `Good` Datetime when PII data is removed from Cosmos
   - *This is a good time because this is when the incident is fully resolved.*

# Impact

## Customer Impact 

**[ ] Description of the user symptoms**
```
Guidelines:
- Must contain descriptions of user scenario impacts (User could not login, user could not at mention)
- Must contain service level impacts (No telemetry for x days)
- Should be specific to the type of user that was affected (Not the number, but describe the type.) Ex. All E3 users or all MSFT users.
- Use quantifying words like: Some, All, Few, Most
- Must specific platform affected if not all (desktop, windows only, iOS)
```
Examples:
- `Good` The user was not able to @mention users
- `Good` The user could do @mentions with a cached user list but search for other users was broken
- `Good` User could log in but was seeing spinners in the giphy dialog
- `Good` There was no telemetry for iOS / Android clients and also stops any monitors for these platforms.
    - *Good because it mentions the platforms*
- `Good` There were periodic spikes in failures to chat service causing some users to fail to send / receive messages
    - *Has quantifying adjective periodic*
- `Good` These are the user features affected by graph outage:
    - stale at mention user list
    - no user search
    - no roster sync
    - no user pictures
- `Bad` API GetUser was failing and returning 500
    - *This is describing an API which is ok, but it doesn't let me know what the user saw*
- `Bad` There were errors to chat service
    - *It's not clear what type of errors and any quantifying adjectives* 
- `Bad` Giphy had an outage and could not be reached
    - *This is close but it still doesn't let me know what was wrong for the user*
- `Bad` Graph API was returning 429 and throttling users for MSFT tenant.
    - *This again is ok that it tells us that it was a problem with the partner but we have no idea what the user saw*

**[ ] Communications**
```
Guidelines:
- List any comms action taken
- List the SHD url used for the incident
```
Example:
- `Good` SHD: http://iridias/Reporting/IncidentLookup/TM105366 
- `Bad` SHD 105366
    - *No easy way to discover and read the post*

## Qos/SLA Impact

**[ ] Produce real number metrics of user impact, this should be detailed and vagueness is not ever desired**
```
Guidelines:
- Must indicate regional vs global vs go-local impact
- Must indicate platform percent affected
- Must indicate at least either tenant numbers or user numbers
- Optional provide unique users
- Estimates are ok for user numbers based on projection
- Percentages are often better than raw numbers both are best
- Duration of impact if it is important for understanding the rate of impact
- Avoid queries these are too specific, but you can include it as an attachment, so we can double check the query results
```
Examples:
- `Good` Impact was global
- `Good` Impact was just to USWE-01 (West coast Americas)
- `Good` 10% of web traffic and 4% of desktop traffic was affected by this change
- `Bad` web traffic and desktop were affected
    - *No indicator how bad the impact was*
- `Mandatory` *1824 tenants (9.6% of all tenants) and 8765 users (1% of all users) during this period*
    - *Real numbers*
    - *Duration also included for context*
- `OK` The number of requests went from 200k to 6M per day
    - *It's good to provide these numbers but they are not a replacement for tenant/user numbers*
- `OK` Almost all of the on-prem autodiscovery calls were failing, but we don't know how many users are on-prem
    - *If it's really specific it's ok to use qualifiers, but you should indicate that we don't have that data* 
- `Bad` Including a kusto query
    - *It's out of context for the post mortem, please add as attachment*

**[ ] Relevant chart/graphs indicating incident measures should be displayed**
```
Guidelines:
- Minimize charts (1 is best)
- Should indicate scale and should have description if not self explanatory
- Should span the entire impact duration if possible
- Should indicate if it is a snapshot (if repeated short outages for example)
- Should indicate scale of impact
```

## Services Responsible

**[ ] Should indicate the Tier 2 team or external service**
Examples:
- `Good` Messaging
- `Good` Admin and Admin portal
- `Good` Chat Service
- `Good` Microsoft Graph
- `Bad` Mountaineers

## Services Impacted

**[ ] You can ignore this field

# Root Cause

**[ ] Root cause title should describe root cause**
```
Guidelines:
- Avoid approximate root cause (bad ex. Commit cause a bug, good ex. Avoiding batch calls increased traffic volume)
- Avoid listing the trigger (bad ex. office rollout caused our settings to break, good ex. Our settings feature was not implemented correctly)
```
Examples:
- `Good` A regression skipped batch processing resulting in 10x increase in partner calls
- `Bad` A regression
- `Bad` A regression to syncroster
   - *Too vague and tribal knowledge and execute can not read that root cause an understand*
- `Bad` A network issue
   - *A network issue can always be broken down into deeper parts like DNS, cabling, a particular DC*
- `Good` A machine outage in USEA-01 for MT caused auth to fail

**[ ] Root cause description**
```
Guidelines:
- The first paragraph should clearly indicate what the root cause of the incident was
- Do indicate if a root cause is preliminary
- Do indicate if a root cause is a best guess/estimate of what happened
- In following paragraphs includes sections if applicable: background leading up, date decisions, reasoning behind best guess
- Do list data points that are relevant
- You must have PR links or commit links for code that causes regression (has to a be link)
- You must have date/time background leading to a config/production change (ie. release date)
- You must indicate if any process(es) were skipped
- You must all root causes if multiple issues contributed to the problem (nothing should be left out)
- (Optional) Provide diagrams if short and appropriate (graphs and charts do not belong here)
```
`Good` Example: [MSA Outage Causes Channel Creation + Notification Outage](https://icm.ad.msft.net/imp/v3/incidents/postmortem/48017)
```
A bad cert rollout at 10:00AM for MSA caused a widespread outage across MSFT that included the S2S communication used by Teams to push notifications from firehose -> Chat and in creating / modifying channels.

(MSA post mortem: https://icm.ad.msft.net/imp/v3/incidents/postmortem/48034)

Teams services talk to Chat Service using a S2S token, these tokens are generated for each instance that talks to Chat Service and they are generated by MSA. This explains the partial outage and not complete for all machines as this only renews on an instance basis.
```

`Good` Example: [sfB interop messages would get reordered if leaving and reenterring session](https://icm.ad.msft.net/imp/v3/incidents/postmortem/47768)
```
​A fix for a bug with inaccurate message order was made on Feb 9 into develop. PR 31408​ and Bug 79772

This bug fix ensured that pending sent messages had their client lie timestamps bumped up whenever an earlier sent message was resolved by the server and a server timestamp given. For example, if user sent messages A B and C, when server gives us timestamp for A then we bump B and C client lie timestamps to be greater than that.

In implementation and testing, we failed to notice that SfB interop messages have an unintended design flaw - all sent messages stay as a client lie and never resolve to "realized" messages. Until this particular case, no one noticed this as it is transparent to the user.

When this fix was made, it had the effect of rewriting timestamps of all​ sent messages in the SfB conversation since the code presumed they had not yet been resolved by the server.
```

`Good` Example: [New users with existing notifications may be unable to see them in the Microsoft Teams client](https://icm.ad.msft.net/imp/v3/incidents/postmortem/47870)
```
There was a design flaw in Feeds architecture where in FRE scenario, we are missing signals which indicate the data store loading dependency.

The issue was reported earlier in this livesite - https://icm.ad.msft.net/imp/v3/incidents/postmortem/48003 and a fix was prepared (https://domoreexp.visualstudio.com/Teamspace/_git/Teamspace-Web/pullrequest/35491?_a=overview) and checked in to develop on 4/15. Unfortunately before the deployment could reach to rings, this livesite happened and we have resolved this with a hotfix of the checked in PR.

Design Flaw:

Notification Store emits an event once the store is ready with notifications fetched and Feeds Controller who has subscribed for it will listen to it and fetch the feeds and render it in the view. During FRE scenario, we have a FRE page which will make the Controller to load later and by the time it subscribes, notification store has already raised the event and controller missed it.

New Design:

We had to expose a promise from Store and Controller consumes it and wait's till it resolved or rejected.
```

`Bad` Example: [Mail queue in Firehose was backed up for days with out detection](https://icm.ad.msft.net/imp/v3/incidents/postmortem/49876)
```
Queue was stagnant for long time (few days), there was no activity in our log, when we were trying to dequeue, we were not seeing any messages even though there were. 

We escalated to Azure, unfortunately, Azure could not investigate on time before the logs rolled over.

Azure ICM: 38151091.

After deployment on the env on 23rd the queue drained instantly
```

Reasoning:
- Description of the problem is short, there are a lot of assumptions about the architecture that are made that non-firehose members would not understand
- Needs a better timeline description of what happened and how the growth of stagnation took place (all at once, gradual)
- Doesn't describe what Azure needed to investigate so its hard to create precise action items
- ICM number is not a link
- Also does not describe any deficiencies in monitoring that lead to the issue

# Detection And Mitigation

## Detection

**[ ] Must fill in this field**
```
Guidelines:
- we only use customer or monitoring
```

**[ ] Add detection detail as is relevant (optional)**

## Mitigation

**[ ] List the final mitigating action**
```
Guidelines:
- List what the action was clearly ex. failover, rollback, hotfix
- Do list if no action was taken and it passed as a transient issue
- You must provide a link to the PRs used in a hotfix
```
Examples:
- `Good` We failed over USEA-01 for MT to USWE-01 until the outlook outage was mitigated
- `Good` We cleared the mailhook queue to unblock the bad request
- `Good` We hotfixed the webclient with PR 34343: http://....

**[ ] All supporting PRs as part of the mitigation are listed with links**
```
Guidelines:
- The links must be provided because the PR could be in different projects (ex. Chat Service)
```
- We hotfixed the webclient with PR 34343: http://....

**[ ] It is required that a date based event timeline of all mitigation actions**
```
Guidelines:
- Some mitigations have different steps all these steps should be listed
- If the mitigation action was wrong or had no effect it should still be listed
- Audits need us to list all the steps taken to address the issue
- Format should be:  MM/DD/YYYY HH:mm: action that was taken and possibly the effect (or non-effect)
```
Example:
- `Good` 03/10/2017 11:23 AM PST - Tried restarting the firehose machines, this only delayed the issue
- `Good` 03/10/2017 1:10 PM PST - Tried adding more machines, this reduced the impacted percent to 5% from 20%
- `Good` 03/10/2017 6:00 PM PST - Hotfix was final mitigation

**[ ] (Optional) It is helpful to add notes here about situational occurrences that were relevant**
```
Guidelines:
- Format should be: Note: description or comment
- These could anything like mitigation still took 2 hours or something else of relevance.
```

## Fix

**Formatting rules:**
```
- Notes should use "Notes: <MM/DD/YYYY HH:mm> <expression>"
- Tasks and bugs should be clickable links
- Tasks and bugs should have a good descriptive title that could be read independently and still understood
- Format for tasks and bugs use "Task 32327: <expression>"
```

**[ ] Must list all post incident actions that were done to fix/resolve the entire issue**
```
Guidelines:
- List all actions (do not assume it is understood what the action was)
- Do not be vague (bad ex. failover, good ex. failed over DM2P to BY3P)
- Use a timeline if relevant (include date and time)
- Include actions that require manual fixes
- Include all PRs that were required to resolve the incident within the incident window (not long term arch fixes)
```
Examples:
- `Good` Note: First action was to restart the machines, but this only bought time before the queue jammed up again
- `Bad` Note: Took a while to find root cause
   - *This note adds nothing productive*

**[ ] List tasks and bugs that will help prevent the incident from occurring**
```
Guidelines:
- This is easiest for the engineer
- Provide PR links if available (must have a link)
- These are often suggestions to fix code
- Provide short term, medium term and long term fixes (provide multiple options instead of one catch all)
- Bug description should be clear (bad ex. fix auth code, good ex. Split out different auth paths into modules)
- Do not list generic testing tasks like better unit testing
- Do list specific testing tasks like adding test cases to the manual test suite
```
Examples:
- `Good` [Task 00000]: Add a unit test for serialization of the custom datetime object    
- `Bad` [Task 00000]: Add unit tests
   - *This is too open ended, the task has no clear completion and is not clear for the dev.*
   - *This allows interpretation and allows weak tests to be added*
- `Good` [Task 00000]: Separate out auth flows into different modules
- `Bad` [Task 00000]: Do better code reviews
  - *Better to have a concrete output, like create code review checklist or have senior devs sign off*
   
**[ ] List tasks to help improve monitoring and detection**
```
Guidelines:
- This is a key factor if detection time was slow
- Do specify specific monitors that need to be added
- Also focus on automation and not manual tasks
- Do improve diagnostic tools like dashboards
- As a rule dashboards are used for diagnostics, monitors will make a phone call
- Do not add tasks that add manual detection (in general are not effective or scale)
- Do include work items that incorporate need sources of monitoring
- Its possible to include cross team monitoring tasks
```
Examples:
- `Good` [Task 00000]: Create a dashboard to indicate all request volumes for graph based MT APIs
- `Good` [Task 00000]: Create a monitor to detect traffic jump by 3x for request volumes for graph based MT APIs
- `Bad` [Task 00000]: Add a monitor for graph
    - *What is the purpose of the monitor it is not clear*
    - *The title of the task should read clearly what is being asked not so generic*
- `Good` [Task 00000]: Add Aria reports from PII scanning
- `Good` [Task 00000]: Write tools to scan cosmos logs for team name

**[ ] List tasks to improve mitigation**
```
Guidelines:
- Simple tasks include adding escalation playbooks
- Complex tasks include adding tools or new processes
- Avoid TSGs that require lots of Kusto queries and lots of interpretation, it should be clear as day what the mitigation is
- Escalation playbooks should always be emphasized
- Add tasks to partners if they need to improve their response (or not meet SLA)
- Include tasks to verify and record partner SLAs
```
Examples:
- `Good` [Task 00000]: Add escalation playbook for new exchange catalog for WOPI services
- `Good` [Task 00000]: Create a dashboard to indicate all request volume for graph based MT APIs
- `Bad` [Task 00000]: Write TSG for monitor
  - *This is very vague, it doesn't indicate the monitor*
  - *This is not followed up by escalation playbooks so there is no guarantee that the TSG leads to a mitigation*
- `Good` [Task 00000]: Follow up with Azure on why their machines CPU thrash for 12 mins during update
- `Good` [Task 00000]: Add a kill switch so we can turn off Google auth and add escalation playbook

