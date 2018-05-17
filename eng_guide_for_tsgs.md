## What is it that I will do?

Assess: the situation by understand the impact, the severity and the scale of the incident

Identify: the issues and symptoms that are being experienced in the incident

Act: to mitigate the user symptoms experienced in the incident

Verify: that the mitigation was complete and that the incident is fully resolved

### Troubleshooting guides (TSGs)

As the DRI you are only really able debug or respond by following trouble shooting guides that are written by the development team. These guides are purely for assessment of the incident, they eventually link to an Escalation Playbook. (See the following section)

#### Searching for a TSG

[Shortcut to TSG](https://aka.ms/st-sre/tsgsearch)

![alt-text](https://domoreexp.visualstudio.com/DefaultCollection/11ac29bc-5a99-400b-b225-01839ab0c9df/_api/_versioncontrol/itemContent?repositoryId=e7e35b30-7782-4e79-a2fd-9f9bf23e1c0e&path=%2Ftsg%2Fimages%2FTSG+search.png&version=GBlive&contentOnly=true&__v=5  "TSG search screenshot")

1. Navigate to the TSG shortcut [https://aka.ms/st-sre/tsgsearch](https://aka.ms/st-sre/tsgsearch)
2. Enter the apiname or scenario in the following search format: ```file:*apiname* or file:*scenario*```
3. This will turn up search results.
4. After finding the right TSG, you can run the kusto query in the TSG to confirm symptoms
5. Sometimes the symptoms require some interpretation so you should follow the TSG instructions to lead you to the mitigation steps.
6. The mitigation steps must be a link to an escalation playbook.
7. These playbooks contain the actions needed to be done to mitigate or escalate an incident
8. ```Note: It is possible that TSGs are missing information, out of date or missing entirely, please use your best judgement to figure out if you need to just escalate to tier 2.```

For example:
```
1. For ticket: [[MT Availability] Teams Channels - Core (50%)] MT Core Availability [skypeteams.prod.asse-02_true_TeamController_GetTeamMembers] is unhealthy.](https://icm.ad.msft.net/imp/v3/incidents/details/42043335/home)
2. We determine the api name is: TeamController_GetTeamMembers
3. So we navigate to [https://aka.ms/st-sre/tsgsearch](https://aka.ms/st-sre/tsgsearch)
4. We search for: file:TeamController_GetTeamMembers
5. We find the TSG and we run the query in the [Kusto Web Explorer](https://aka.ms/st-sre/kwe)
6. We take a screenshot and post the search results in the SRE bridge.
7. We look at the TSG and it points out that most of the errors are 500 which leads to escalate to Chat Service.
8. We then follow the link to escalate to Chat Service
9. Finally in this assessment stage we record what we did back in the SRE bridge.
```

#### Components of a TSG

1. The title that contains the scenario or apiname
2. Kusto query to determine user impact (user symptoms), you should be confortable enough to expand a request query into a distinct user count or distinct tenant count.
3. Some Kusto queries don't have the database you need to query so ask for help if you don't know
4. Some TSGS also have a dashboard you can view to see health over time according to values important to the development team.
5. Some TSGs would them map your search results to escalation playbook link. 
6. Other details are included in the TSG, include exceptions or known issues for which the ticket should not follow mitigation.

![alt-text](https://domoreexp.visualstudio.com/DefaultCollection/11ac29bc-5a99-400b-b225-01839ab0c9df/_api/_versioncontrol/itemContent?repositoryId=e7e35b30-7782-4e79-a2fd-9f9bf23e1c0e&path=%2Ftsg%2Fimages%2Ffile-TeamController_GetTeamMembers+-+Search+Code+-+Visual+Studio+Team+Services.png&version=GBlive&contentOnly=true&__v=5  "Part 1")
![alt-text](https://domoreexp.visualstudio.com/DefaultCollection/11ac29bc-5a99-400b-b225-01839ab0c9df/_api/_versioncontrol/itemContent?repositoryId=e7e35b30-7782-4e79-a2fd-9f9bf23e1c0e&path=%2Ftsg%2Fimages%2Ffile-TeamController_GetTeamMembers+-+Search+Code+-+Visual+Studio+Team+Services+part+2.png&version=GBlive&contentOnly=true&__v=5  "Part 2")


