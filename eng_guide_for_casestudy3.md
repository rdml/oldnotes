## What is it that I will do?

Assess: the situation by understand the impact, the severity and the scale of the incident

Identify: the issues and symptoms that are being experienced in the incident

Act: to mitigate the user symptoms experienced in the incident

Verify: that the mitigation was complete and that the incident is fully resolved

## Basic procedure for responding to an alert

1. You'll get a ticket
    - either a phone call
    - or by checking in ICM
2. Acknowledge the ticket if you are going to response
    - you should not acknowledge if you are not able to drive the incident response
3. Go to the SRE Bridge and create a new message thread
    - set the subject to the Severity and title of the title
    - set the body to the hyperlink to the ICM ticket
4. Search for a TSG
5. Follow the queries in the TSG
    - TSG might have you look at dashboards as well
    - you should post your results in the bridge
6. Identify the problem
7. Follow the mitigation steps in the TSG
8. If you cannot find the TSG you should escalate to the tier 2 team (call them)
9. Continue to force investigation and drive mitigation
10. Confirm mitigation of user symptoms
11. Mitigate the ticket
12. Resolve the ticket
13. Create a post mortem
14. Cleanup livesite quality ** These are tasks like: updating TSGs, monitors or changing monitor thresholds**

![alt-text](https://domoreexp.visualstudio.com/DefaultCollection/11ac29bc-5a99-400b-b225-01839ab0c9df/_api/_versioncontrol/itemContent?repositoryId=e7e35b30-7782-4e79-a2fd-9f9bf23e1c0e&path=%2Fsre_guides%2Fimages%2Fbasic_incident_response.png&version=GBlive&contentOnly=true&__v=5 "Basic flow")

## Receiving a sev 2 PII alert

Group A: 

- [Template to start an incident workflow](https://aka.ms/st-sre/training/a/sev3pii)
- [Training On-Call List](https://icm.ad.msft.net/imp/v3/oncall/current?categoryId=0&serviceId=20592&teamIds=24825&scheduleType=timeline&shiftType=current&viewType=1&gridViewStartDate=2017-07-19T07:00:00.000Z&gridViewEndDate=2017-07-25T07:00:00.000Z&gridViewSelectedDateRangeType=4)

Group B: 

- [Template to start an incident workflow](https://aka.ms/st-sre/training/b/sev3pii)
- [Training On-Call List](https://icm.ad.msft.net/imp/v3/oncall/current?categoryId=0&serviceId=20592&teamIds=24825&scheduleType=timeline&shiftType=current&viewType=1&gridViewStartDate=2017-07-19T07:00:00.000Z&gridViewEndDate=2017-07-25T07:00:00.000Z&gridViewSelectedDateRangeType=4)

Group C: 
- [Template to start an incident workflow](https://aka.ms/st-sre/training/c/sev3pii)
- [Training On-Call List](https://icm.ad.msft.net/imp/v3/oncall/current?categoryId=0&serviceId=20592&teamIds=24825&scheduleType=timeline&shiftType=current&viewType=1&gridViewStartDate=2017-07-19T07:00:00.000Z&gridViewEndDate=2017-07-25T07:00:00.000Z&gridViewSelectedDateRangeType=4)

Group D: 

- [Template to start an incident workflow](https://aka.ms/st-sre/training/d/sev3pii)
- [Training On-Call List](https://icm.ad.msft.net/imp/v3/oncall/current?categoryId=0&serviceId=20592&teamIds=24825&scheduleType=timeline&shiftType=current&viewType=1&gridViewStartDate=2017-07-19T07:00:00.000Z&gridViewEndDate=2017-07-25T07:00:00.000Z&gridViewSelectedDateRangeType=4)

### Exercise:

#### Receiving a PII alert and acknowledging the ticket

1. Confirm that there is an on-call and that it is correct [Training On-Call List](https://icm.ad.msft.net/imp/v3/oncall/current?categoryId=0&serviceId=21215&teamIds=0&scheduleType=timeline&shiftType=current&viewType=1&gridViewStartDate=2017-07-19T07:00:00.000Z&gridViewEndDate=2017-07-25T07:00:00.000Z&gridViewSelectedDateRangeType=4)
2. Substitute your team if it is not currently on there
  - Click on the engineer you want to replace
  - Click "add substitute"
  - Select the engineer to substitute
  - Leave the rest of the settings (for this tutorial only)
  - Save
3. Use the template above to trigger a sev 3
4. Team members should check their training group queue to see when the ticket appears.
5. There will be no phone call so you will find these explicitly.
6. The person who will create the bridge will acknowledge, notice the others will not acknowledge.

```
Note there are several ways to acknowledge the incident:
1. If you receive a phone call, you can follow the prompt and input the keypad values to acknowledge.
2. If you receive a text, follow the url and fill out the form to acknowledge.
3. If you receive a text or phone call you can acknowledge by finding the ticket in the phone app and acknowledge
4. If you receive a text or phone call you can acknowledge by finding the ticket in the icm portal (https://aka.ms/icm) and acknowledge
```

When you acknowledge a ticket you are responsible for the following:
1. You must create the SRE bridge message thread for the incident
2. You are the investigator by using the TSG until a tier 2 acknowledges and starts to investigate (positive handoff)
3. You are responsible for getting comms if it is appropriate
4. You are responsible for getting IMs if it is appropriate

#### Make sure your hardware is ready

If you are on the road.
1. Make sure that you have a good internet connection.
2. Make sure you have your hotspot out and ready to connect to your laptop.
3. Cell phone hotspots generally do not have high enough bandwidth to use Jarvis so be aware

#### Creating an SRE bridge for the incident

```DO NOT CREATE BRIDGE IN SRE BRIDGE```

PII and Security issues are need to know only, we have a special bridge for that information.

To create the bridge:
1. Transfer the ticket to:
- Service: Skype Teams
- Team: Security
2. Wait for acknowledgement of the ticket
3. The Skype IM team will create the bridge in the private "Teams Security And Privacy Bridge"
4. You will get at mentioned and added to the team
5. The proper security and privacy folks will be added and now you can drive the incident

```
Note: if you are not sure if a bridge already exists, take the ICM ticket number (ex. 42211729) and do a search for it. We should only ever have one ticket.
```

#### Request assistance for external communications to partners

```Note: most incidents that are sev 3 don't really need comms```

1. For any major user impact (for example: failure to auth, broken calls) we need to post external comms to our partners.
2. In the ICM portal, find your active ticket and view the details page.
3. On the right most upper middle of the page is a button for "... More".
4. This dropdown menu will have the option to "Request assistance", click this.
5. This will open a dialog.
    - The description should include a request for comms
    - The Service Category: is Skype
    - The Sevice: is Skype Incident Management
    - The Team: is Skype IM Team
6. This will trigger a phone call to the Skype IM team which will join the bridge based on the ticket number.
7. Their first action is to ask you to fill out the comms template.
8. You can get this information from a combination of TSG and ticket information. See next section on finding a TSG
9. If you cannot answer these questions, immediately reach out to the Tier 2 on-call for this scenario.

Comms Template
**Start Time: **
**User Experience: ** 
**Impact: **
**Caught By: **

An example of a filled out comms request:
```
Start Time: 7/13 12:28 PM PST
User Experience: Users may be unable to sign in or delayed sign in
Impact: Forest 1A
Caught By: Monitoring
```

#### PII TSGs

You will not need to search for these TSGs, please use the below TSGs to handle the incident:

[PII Escalation Playbook](https://domoreexp.visualstudio.com/DefaultCollection/Teamspace/_git/SkypeTeams-SRE?path=%2Fescalation_plays%2Fescalate_to_handle_PII_Incident.md&version=GBlive&fullScreen=true&_a=preview)

#### Escalating to tier 2

Tier 2 are the weekly oncall engineers for the special feature teams. 

![alt-text](https://domoreexp.visualstudio.com/DefaultCollection/11ac29bc-5a99-400b-b225-01839ab0c9df/_api/_versioncontrol/itemContent?repositoryId=e7e35b30-7782-4e79-a2fd-9f9bf23e1c0e&path=%2Fsre_guides%2Fimages%2FOnCall+-+IcM.png&version=GBlive&contentOnly=true&__v=5 "Tier 2 on-call list")

After you determined the approximate feature area look at the [oncall rotation page](https://icm.ad.msft.net/imp/v3/oncall/current?categoryId=0&serviceId=21215&teamIds=0&scheduleType=timeline&shiftType=current&viewType=1&gridViewStartDate=2017-07-17T07:00:00.000Z&gridViewEndDate=2017-07-23T07:00:00.000Z&gridViewSelectedDateRangeType=4)
1. Find the team that you are looking for.
2. At mention them both in the bridge.
3. If the incident is sev 2 or higher and it is after hours it requires a phone call to confirm they see the bridge.
4. If it is a sev 1 regardless of time you must also follow with phone call or personally pull them out of meetings. (I have personally pulled folks out of meetings with the CVP so do not hesitate)

If you are really in trouble here are some folks you should contact:
1. [SRE on-call](https://icm.ad.msft.net/imp/v3/oncall/current?categoryId=0&serviceId=21215&teamIds=32691&scheduleType=timeline&shiftType=current&viewType=1&gridViewStartDate=2017-07-19T07:00:00.000Z&gridViewEndDate=2017-07-25T07:00:00.000Z&gridViewSelectedDateRangeType=4) (This is the MS Teams on-call, your main go to team) Located only in Bellevue (so be nice)
2. [Skype IM](https://icm.ad.msft.net/imp/v3/oncall/current?categoryId=0&serviceId=20592&teamIds=24825&scheduleType=timeline&shiftType=current&viewType=1&gridViewStartDate=2017-07-19T07:00:00.000Z&gridViewEndDate=2017-07-25T07:00:00.000Z&gridViewSelectedDateRangeType=4) (This is our SRE sister team under Skype) Located globally with 24 hour rotation
3. [IM (Incident Manager)](https://icm.ad.msft.net/imp/v3/oncall/current?categoryId=0&serviceId=21215&teamIds=28401&scheduleType=timeline&shiftType=current&viewType=1&gridViewStartDate=2017-07-19T07:00:00.000Z&gridViewEndDate=2017-07-25T07:00:00.000Z&gridViewSelectedDateRangeType=4) (This is the GEM on the MS Teams, they are on-call to make sure you have the resources to make the right decision and escalate to the right help) Available 24 hours 

#### Checking for mitigation

After the mitigation is applied you or the tier 2 oncall need to verify the symptoms have mitigated. It is helpful to post a screenshot of the queries you are running to show mitigation. Mitigation is when the user symptoms have subsided back to SLA levels.

1. At this point you should go into ICM and link all the related tickets to the **first** ticket to be fired.
2. You can click on the only ticket left (the master ticket)
3. On this page you will see a button called "Mitigated"
4. Click on this and you will get a page for you to fill out the mitigation.
5. Do put details of how the issue was mitigated, links to bugs or hotfix PRs and anyone that might have helped. Even if it was mitigated by waiting it out you should state this. 
6. Selection a category of root cause. Common examples are: human - error defect, human - integration issue, etc.
7. Then (very important) you must check the radio if there was any customer impact. This will automatically require a post mortem.
8. In some cases if there was no user impact but the ticket was a sev 2 or higher, you can leave the ticket as no user impact, but you must select "Require root cause"
9. Otherwise it is ok to select "auto resolve"

#### Resolving a ticket

![alt-image](https://domoreexp.visualstudio.com/DefaultCollection/11ac29bc-5a99-400b-b225-01839ab0c9df/_api/_versioncontrol/itemContent?repositoryId=e7e35b30-7782-4e79-a2fd-9f9bf23e1c0e&path=%2Fsre_guides%2Fimages%2FIncident-42505899+Details+-+IcM.png&version=GBlive&contentOnly=true&__v=5 "Resolving a ticket")

1. If you followed the steps above you will end up with "orange" status tickets that are mitigated.
2. This tickets MUST be resolved before the end of the week. Best policy is to resolve immediately after mitigation so you don't forget.
3. If you click to open a mitigated ticket.
4. Find and click the resolve button.
5. Check the radio that requires "Create Root Cause?": Create New
6. Select a root cause category and also input a Root cause title. If you don't know TBD is good for now.
7. TBD is also good the description
8. Hit "resolve" button to resolve the ticket.

#### Creating a post mortem

1. After you have resolved a ticket you must also create a post mortem if there was any user impact.
2. Find the ticket you just resolved.
3. Click on the "Post Mortem" tab
4. Here you will have a big button to create a new post mortem.
5. It is important that you rename the ticket to something that represented the user symptoms. [See Post Mortem Guidelines](https://aka.ms/st-sre/guidelines)
6. Click "Save and Continue"
7. ```Important``` You only need to do this once the feature team will be responsible for the rest.


