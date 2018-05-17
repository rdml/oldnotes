## What is it that I will do?

Assess: the situation by understand the impact, the severity and the scale of the incident

Identify: the issues and symptoms that are being experienced in the incident

Act: to mitigate the user symptoms experienced in the incident

Verify: that the mitigation was complete and that the incident is fully resolved

### ICM (InCident Management Portal)

You need to use ICM to track the progress of the incident response during the bridges. It is the single source of truth that is shared company wide and provides you the starting point of your investigation and mitigation as well as tracking actions like post mortems after the incident is mitigated. It is the bread and butter of the DRIs action list and you will be checking on it daily basis. 

ICM will:
```
- notify you when a ticket is created
- show you all the active incidents
- show you all the failures that monitors have determined to be unhealthy
- show you which incidents to work on first (severity level)
```

Your top priorities in ICM are:
```
1. Acknowledge new active incidents
2. Make sure there is at least one ticket tracking a particular incident
3. Make sure you drive mitigation of active tickets
4. Make sure you link tickets correctly so there is only one ticket per incident
5. Make sure false alarms are dealt with so that they do not reoccur
6. Make sure the ticket queue is clean (to avoid missing new issues or more important issues)
7. Make sure the mitigated tickets are resolved with post mortem if necessary

As primary and secondary your responsibilities are to make sure you keep this queue clean and tidy all week long so any SRE can come in and assist you if necessary. Clutter usually means we have a poor handling on the livesite and will make your life harder this week.
```

[ICM portal](https://aka.ms/st-sre/tier1)

[Prerequisites](https://domoreexp.visualstudio.com/DefaultCollection/Teamspace/_git/SkypeTeams-SRE?path=%2Fsre_guides%2Fsetup_permissions.md&version=GBlive&fullScreen=true&_a=contents)

#### How to access ICM

You can access the full ICM feature set can be via the [web portal](https://aka.ms/icm). This will have the most functionality. By default you'll have an empty query for your tickets. The following options help you get the right query because the fields can change over time.

The easiest way for you to get to access to the tier 1 live site queue is via the aka link:
[https://aka.ms/st-sre/tier1](https://aka.ms/st-sre/tier1)
We've saved this handy link and keep it updated with new services.

The shared query way to get the tier 1 queue is:
1. Click on the ICM tab or navigate to [https://icm.ad.msft.net/imp/v3/incidents/search/basic](https://icm.ad.msft.net/imp/v3/incidents/search/basic)
2. On the left hand panel click the "Advanced" tab
3. Expand the "Shared Queries"
4. Expand the "Skype Teams" (If this is not here you can't continue and are not a part of this team)
5. Expand the "Skype Teams Tier 1 DRI"
6. Click on the "default" option

One convienent new way to access ICM are new (prototype) iOS and Android applications. [Instructions for downloading ICM app](https://icm.ad.msft.net/imp/v3/support/Mobile-Application/Home)

Once the app is downloaded and installed on your phone, you'll need to get a working query.
1. Click on hamburger button in top left corner
2. Click on the "Queries" tab
3. Expand "Shared Queries"
4. Expand "Skype Teams Tier 1 (Default DRI)"
5. Click on "default"


#### How to acknowledge a ticket

1. Via email: the email will provide a link to the ticket. Click on the link and then click on the "acknowledge" button.
2. Via sms/text: the sms will have two links for acknowledging, click on the acknowledge link and then submit on the webpage that loads on your phone
3. Via phone call: the phone call will have an automated message, follow the prompt by pressing 1, then pressing 1 to acknowledge, you must stay on the phone until "your choice has been acknowledged" is spoken or it is not recorded
4. Via ICM app: in the app click on the ticket and then click on the "hand" symbol to acknowledge the incident
5. Via ICM portal: in the tier 1 queue, click on the unacknowledged ticket and then click on the "acknowledge" button


#### What does the tier 1 queue look like?

You will be looking at the tier 1 queue almost hourly during your primary week (office hours) and on a daily basis if you are secondary. The queue will be either sorted by creation date so it is important to keep the queue clean and free of mitigated tickets. There is no sorting, but you can change the query to filter out or filter in different ticket types. If you get lost use the shortcut to restore your query: [https://aka.ms/st-sre/tier1](https://aka.ms/st-sre/tier1)

Important concepts:

Severity of tickets determines things like response time and if you will get phone calls. So where do the severities come from? The short answer is that the monitors are derived from a matrix called the [Severity Matrix]() that correlates incident impact with scenario importance to determine the severity level. There are some minor heuristics involved to but in general these were the guidelines that set the initial ticket severities.

Some examples are:
100% of iOS users cannot send messages

```
Decision tree:
1. impact is tier 1 because 100% of a platform or region are affected
2. scenario is a dialtone scenario (message send)
3. So result is that this is a severity 1 incident
```
![alt-text](https://domoreexp.visualstudio.com/DefaultCollection/11ac29bc-5a99-400b-b225-01839ab0c9df/_api/_versioncontrol/itemContent?repositoryId=e7e35b30-7782-4e79-a2fd-9f9bf23e1c0e&path=%2Ftsg%2Fimages%2FSkype+Teams+Severity+Matrix+August+2016.xlsx.png&version=GBlive&contentOnly=true&__v=5 "Severity 1 incident for 100% of iOS users cannot send messages")

10% of users can't view their files

```
Decision tree:
1. impact is a tier 2 because 10% of users is within the tier 2 of 10-25% user impact
2. scenario is a optimal scenario
3. So result is that this is a severity 3 incident
```
![alt-text](https://domoreexp.visualstudio.com/DefaultCollection/11ac29bc-5a99-400b-b225-01839ab0c9df/_api/_versioncontrol/itemContent?repositoryId=e7e35b30-7782-4e79-a2fd-9f9bf23e1c0e&path=%2Ftsg%2Fimages%2FSkype+Teams+Severity+Matrix+August+2016sev3.png&version=GBlive&contentOnly=true&__v=5 "Severity 3 incident for 10% of users can't view their org char")

```
**IMPORTANT TO NOTE**:
- manually reported tickets will often not be the right severity at first
- some tickets might be marked lower than they should be so if you question the severity error on the side of caution and raise it up a level
```

**Severity**: (Integer from 1 to 4) This indicates the impact level of the incident. This is also tied to a responsiveness level that is determined by our SLA. In general we want to assess the ticket to right severity so that we have the proper response. For example, it would be inapproprate to have 24x7 urgency to fix a CSS bug with a button.

![alt-text](https://domoreexp.visualstudio.com/DefaultCollection/11ac29bc-5a99-400b-b225-01839ab0c9df/_api/_versioncontrol/itemContent?repositoryId=e7e35b30-7782-4e79-a2fd-9f9bf23e1c0e&path=%2Ftsg%2Fimages%2FIncidents+Search+-+IcM.png&version=GBlive&contentOnly=true&__v=5 "Example of the tier 1 live site queue")

Your response for a:
```
Severity 1 
    - should be to make sure there is investigation or mitigation with a 24x7 activity window
    - should ensure all teams that can contribute or assist in the incident are brought into the conversation (ie. all hands on deck)
    - should make sure there are updates either verbal or via the bridges every 10-30 mins to stress the urgency of live updates
    - should engage Skype IM to make external communications posts to customers and assist Skype IM in what ever information is needed to make the post
    - should make sure there is always at least one point person on the incident such that if some needs a break there is a positive handoff to another responsible person
    - should escalate to partners when it is applicable (sev 1 incidents often involve external partners)
```

```
Severity 2
    - should be to make sure there is investigation or mitigation with a 24x7 activity window
    - should ensure all teams that can contribute or assist in the incident are brought into the conversation (ie. all hands on deck)
    - should engage Skype IM to make external communications posts to customers and assist Skype IM in what ever information is needed to make the post
    - should make sure there is always at least one point person on the incident such that if some needs a break there is a positive handoff to another responsible person
```

```
Severity 3
    - should be to make sure there is investigation or mitigation during office hours
    - should ensure that the tier 2 teams treats this as their primary work for the day (priority is above feature or bug work)
    - should make sure there are updates either verbal or via the bridges at least in the morning or the end of day
    - should engage Skype IM if it is necessary to make external communications posts to customers and assist Skype IM in what ever information is needed to make the post
```

```
Severity 4
    - should be to make sure there is investigation or mitigation during office hours and can take several days
    - should ensure that the tier 2 teams tracks this as a top priority bug
    - should make sure there are updates either verbal or via the bridges at least in the morning or the end of day
    - does not need external communications to customers
```


**Title**: (String in freeform or monitor template) This title is a summary of what might be happening. 

There are 3 types of tickets that can be created:
1. Manual or freeform
    - these are often UI bugs
    - these can be login issues that are hard to monitor
    - these need to be accessed if they are only a single or < 5 tenants (Ranger's queue instead)
    - these often don't have correct severity
    - these can be master tickets that have been renamed
2. Jarvis monitor
    - these are the most common type of ticket
    - they have a pattern that is in the form "[monitor name] scenario [metadata] trailing descriptor"
    - these can come in different severities
    - mostly good severities
    - worst case is a high severity (1 or 2) is originally set as sev 3 or 4
    - there can be many that arrive at the same time if incident is large enough
3. Thousand Eyes Probe
    - these happen infrequently
    - the title will be in this format: "Alert for Skype Teams - https://settings.teams.skype.com/apac/v1.0/health"
    - example: [https://icm.ad.msft.net/imp/v3/incidents/details/40805946/home](https://icm.ad.msft.net/imp/v3/incidents/details/40805946/home)

**State**: this expresses what stage in the incident response this ticket is currently at. 

There are 3 types that matter to us:
1. Active
    - this could be acknowledged or unacknowledged
    - usually only acknowledge if you are going to handle the ticket otherwise leaving it unacknowledged means your backup or someone else can handle it
    - this means the incident is not mitigated and is still impacting users
    - this is the default stage
    - it is ok to re-activate a ticket if symptoms start reoccurring
    - it is typical to leave a ticket active if it will continue to repeat until final mitigation
2. Mitigated
    - this state is set after all user symptoms are again below SLA (in general no more user impact)
    - tickets should not remain in mitigated for long and DRI should drive towards the resolved state
    - tickets in this state might mean that we are unsure of the mitigation and are waiting for repeat
    - DRI often leave tickets in this state but that is not correct and should drive resolution
3. Resolved
    - final state of the ticket
    - tickets should be here if the incident was mitigated and no more repeat incidents
    - general rule for us is to get to this state as early as possible (this is for book keeping reasons, livesite is still about mitigation)
    - when coming to this state the DRI needs to access if it is post mortem worthy
    - see section "Resolving tickets" for more about deciding if an incident is worthy of post mortem, simple rule is any real user impact needs a post mortem

How these break down in the real world:
1. You'll first get an ```active``` ticket that is unacknowledged.
2. If it is a sev 2 or higher you will receive a sms text or a phone call that says the number of the ticket and you follow the instructions to acknowledge
3. Alternatively you can go into ICM and find the sev 2 or sev 1 that made the call and click on the ticket, then click "acknowledge"
4. If its a sev 3 you'll find those in your tier 1 by checking periodically. Again click on the ticket, then click "acknowledge"
5. To mitigate, find the ticket for that incident in the tier 1 queue and click on the ticket, then click "mitigate"
6. Fill in the mitigate steps that were taken and indicate if there was user impact
7. To resolve, find the ```mitigated``` ticket from the tier 1 queue and click on the ticket, then click "resolve"
8. Fill in the form and indicate if there was use impact.
9. At this point the ticket is ```resolved``` and in the final state.


**Hit Count**: Not the most important value but you can use this measure to understand if repeats will keep happening

```
That covers this section, what have we learned:
- We know how to access ICM
- We know how to get the tier 1 query
- We know how to read and scan the ticket list
- We understand the differences between severities
- We got some preliminary rules about classifying tickets by their title
- We understand the ticket workflow from Active/unacknowledged to Resolved

We will go further and go through the details of a ticket and handling an incident at a later section.
```


