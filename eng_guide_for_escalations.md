## What is it that I will do?

Assess: the situation by understand the impact, the severity and the scale of the incident

Identify: the issues and symptoms that are being experienced in the incident

Act: to mitigate the user symptoms experienced in the incident

Verify: that the mitigation was complete and that the incident is fully resolved

### Escalation playbooks 

Escalation playbooks are action that you as the DRI can take to escalate or mitigate an issue. You will get to these either by following a TSG or directed to by a tier 2 on call investigator. 

The way you read the title is: escalate_to_(service, feature team or product)_possible_(action)

1. Service are the name of the service you will want to escalate to
    - examples are: AAD, Calling, Siphon, Security
2. Actions are the mitigation or escalate steps you want to request form that service
    - examples are: rollback, failover, config update, etc.

#### Categories of Escalation Playbooks

![alt-text](https://domoreexp.visualstudio.com/DefaultCollection/11ac29bc-5a99-400b-b225-01839ab0c9df/_api/_versioncontrol/itemContent?repositoryId=e7e35b30-7782-4e79-a2fd-9f9bf23e1c0e&path=%2Fsre_guides%2Fimages%2Fescalate_to_aad_graphApi.md+-+Visual+Studio+Team+Services.png&version=GBlive&contentOnly=true&__v=5 "Partner ICM")
1. Simple instructions to create an ICM ticket with the partner
    - Use this find a template or a instructions how to fill in a template for an ICM ticket to the partner
    - Sometimes will contain examples of data points that are needed for the partner ticket like session ids

![alt-text](https://domoreexp.visualstudio.com/DefaultCollection/11ac29bc-5a99-400b-b225-01839ab0c9df/_api/_versioncontrol/itemContent?repositoryId=e7e35b30-7782-4e79-a2fd-9f9bf23e1c0e&path=%2Fsre_guides%2Fimages%2Fescalate_to_botsserver_possible_cache_reboot.md+-+Visual+Studio+Team+Services.png&version=GBlive&contentOnly=true&__v=5 "SRE")
2. Instructions which require you to contact the SRE oncall to take action (due to permissions)
    - These are actions that only SRE have permissions to do
    - They always involve our own infrastructure as opposed to partners
    - Simply call the on-call SRE (not at mention) and get them up to date with the action
    - You can skip the instructions below the SRE oncall because those are for SREs

![alt-text](https://domoreexp.visualstudio.com/DefaultCollection/11ac29bc-5a99-400b-b225-01839ab0c9df/_api/_versioncontrol/itemContent?repositoryId=e7e35b30-7782-4e79-a2fd-9f9bf23e1c0e&path=%2Fsre_guides%2Fimages%2Fescalate_to_android_possible_investigation.md+-+Visual+Studio+Team+Services.png&version=GBlive&contentOnly=true&__v=5 "Feature team")
3. Simple instructions to bring in the tier 2 team oncall
    - Some escalations are simply to escalate to a feature team
    - Escalate to extensibility for giphy for example because they have direct contacts


