## What is it that I will do?

Assess: the situation by understand the impact, the severity and the scale of the incident

Identify: the issues and symptoms that are being experienced in the incident

Act: to mitigate the user symptoms experienced in the incident

Verify: that the mitigation was complete and that the incident is fully resolved

### Microsoft SRE Bridge

#### Creating an SRE bridge for the incident
 
1. In a web browser, navigate to the [SRE bridge General channel](https://teams.microsoft.com/_#/conversations/General?threadId=19:5bdd2dfb85d74e428ef2c147d370f021@thread.skype&ctx=channel)
2. In a separate tab, open the ICM portal and find your active ticket. Click to open the details.
3. In Teams product, create a new thread and expand the advanced compose.
4. For the subject put in the Severity and the Title of the ticket. *for example: Sev 2 : [SRE - 5xx Response Codes] API.Scenario.Environment.ResponseCode [skypeteams.prod.uswe-01_UserController_GetAppEntitlements_500] is unhealthy.*
5. In the body the first detail must be the url for the ICM ticket. *For example: https://icm.ad.msft.net/imp/v3/incidents/details/42211729/home* This is used by search to find the bridge by all parties.
6. Send this message to start the bridge.

```
Note: if you are not sure if a bridge already exists, take the ICM ticket number (ex. 42211729) and do a search for it. We should only ever have one ticket.
```

#### What is a bridge?

![alt-text](https://domoreexp.visualstudio.com/DefaultCollection/11ac29bc-5a99-400b-b225-01839ab0c9df/_api/_versioncontrol/itemContent?repositoryId=e7e35b30-7782-4e79-a2fd-9f9bf23e1c0e&path=%2Fsre_guides%2Fimages%2Fsre_bridge_example.png&version=GBlive&contentOnly=true&__v=5 "Example of a sev 2 bridge")

A bridge for us is a common place to do all the incident communication. In the past Microsoft has used Skype for Business and Skype Consumer for these tasks, but all Skype and Teams bridges use [Microsoft Teams](https://teams.microsoft.com).

[SRE bridge General channel](https://teams.microsoft.com/_#/conversations/General?threadId=19:5bdd2dfb85d74e428ef2c147d370f021@thread.skype&ctx=channel)

A bridge is specifically a ```message thread```. The bridge team is called "Teams SRE Bridge", there are on-call SRE in Skype IM and Teams that are owners and can add new members, feel free to contact any of them to add new people. 

1. Every incident should have only one bridge
2. A bridge can track multiple ICM tickets (notice that a single incident can trigger many tickets, its often common for us to create tickets to other partners as well)
3. A bridge title should be the message subject
4. The bridge title MUST contain the severity of the ticket
5. The title should be descriptive of the incident, it is ok to take the ICM title for speed reasons, but try to update this later
6. A link to the ICM ticket MUST be somewhere in the thread.

#### Bridge participants

Anyone that can help with the mitigation or incident response is welcome to join the bridge. Here are some categories:
1. The on-call tier 1 DRI
2. The on-call tier 2 DRI
3. Skype IM 
4. SHD Comms people
5. The manager of the tier 2 team
6. The on-call IM (GEM of Microsoft Teams)
7. Program managers (rarely)
8. Executives (Jigar, Brian) only for sev 0 tickets
9. Partner team on-call engineers

#### Closing a bridge

We close our bridges after mitigation or resolution is done. Once we have fully confirmed the incident is over, we notify people that the bridge is closed and no updates are expected, by sending a final message:
1. Text: ****** CLOSED ******
2. Bold
3. Red color


