
# Engineers Guide for Primary Teamwide On-Call

The purpose of this guide is to detail a course that will walk DRI's through the oncall role and responsibility. In the following we will have drills and live exercises so folks can experience the cases first hand and get practice as well as learn the procedures. Your role is critical the functioning of the team and beyond picking up a phone you'll play a major role in the engineering health of the entire product.

## This course will run through 2 days:
1. Tools walkthrough and basic procedures
2. Case study: Covering incident alarms


#  Boil it down for me....

## What is it that I will do?

Assess: the situation by understand the impact, the severity and the scale of the incident

Identify: the issues and symptoms that are being experienced in the incident

Act: to mitigate the user symptoms experienced in the incident

Verify: that the mitigation was complete and that the incident is fully resolved

## How will I do it?

```Assess``` YOU WILL RESPOND: to problem symptoms alerts, user feedback or product team

```Identify``` YOU WILL COORDINATE: incident assessment by using Teams and the SRE bridge and the ICM ticket

```Act``` YOU WILL ESCALATE: bring in help to mitigate the problems

```Verify``` YOU WILL VERIFY: that the problem symptoms are actually subsided

```Close``` YOU WILL RESOLVE: the ticket and produce post mortems

![alt-text](https://domoreexp.visualstudio.com/DefaultCollection/11ac29bc-5a99-400b-b225-01839ab0c9df/_api/_versioncontrol/itemContent?repositoryId=e7e35b30-7782-4e79-a2fd-9f9bf23e1c0e&path=%2Fsre_guides%2Fimages%2Fdinosaur-overview.png&version=GBlive&contentOnly=true&__v=5 "Incident response overview")


# Tools walkthrough and basic procedures

## Tools of the trade

These tools we will cover help us with these core responsibilities:
- monitoring
- incident management
- probing

### ICM (InCident Management Portal)

[Let's take a look at ICM]()

### Jarvis (aka. MDM, Geneva)

### Thousand Eyes (3rd Party External Probe)

### Kusto (Kusto Web Explorer)

[Prerequisites](https://domoreexp.visualstudio.com/DefaultCollection/Teamspace/_git/SkypeTeams-SRE?path=%2Fsre_guides%2Fsetup_permissions.md&version=GBlive&fullScreen=true&_a=contents)

We will be following up with a separate training course for using Kusto.

1. For now the easiest way to access Kusto is the web browser: [https://aka.ms/st-sre/kwe](https://aka.ms/ke). This is good for all OSs
2. For windows machines, accessing Kusto via [https://aka.ms/ke](https://aka.ms/ke). This will require corp access.

### Aria

[Prerequisites](https://domoreexp.visualstudio.com/DefaultCollection/Teamspace/_git/SkypeTeams-SRE?path=%2Fsre_guides%2Fsetup_permissions.md&version=GBlive&fullScreen=true&_a=contents)

We will be following up with a separate training course for using Aria.

Access it by: [https://aria.microsoft.com](https://aria.microsoft.com)

### Microsoft SRE Bridge

### Troubleshooting guides (TSGs)

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


# Exercises: Covering incident alarms

## Receiving a sev 2 availability alert

## Receiving a sev 2 error count alert

## Receiving a sev 2 PII alert

## Receiving a customer support ticket (Rangers)

## Receiving a sev 3 alerts


