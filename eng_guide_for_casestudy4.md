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

## Receiving a customer support ticket (Rangers)

Group A: 

- [Template to start an incident workflow](https://aka.ms/st-sre/training/a/sev3rangers)
- [Training On-Call List](https://icm.ad.msft.net/imp/v3/oncall/current?categoryId=0&serviceId=20592&teamIds=24825&scheduleType=timeline&shiftType=current&viewType=1&gridViewStartDate=2017-07-19T07:00:00.000Z&gridViewEndDate=2017-07-25T07:00:00.000Z&gridViewSelectedDateRangeType=4)

Group B: 

- [Template to start an incident workflow](https://aka.ms/st-sre/training/b/sev3rangers)
- [Training On-Call List](https://icm.ad.msft.net/imp/v3/oncall/current?categoryId=0&serviceId=20592&teamIds=24825&scheduleType=timeline&shiftType=current&viewType=1&gridViewStartDate=2017-07-19T07:00:00.000Z&gridViewEndDate=2017-07-25T07:00:00.000Z&gridViewSelectedDateRangeType=4)

Group C: 
- [Template to start an incident workflow](https://aka.ms/st-sre/training/c/sev3rangers)
- [Training On-Call List](https://icm.ad.msft.net/imp/v3/oncall/current?categoryId=0&serviceId=20592&teamIds=24825&scheduleType=timeline&shiftType=current&viewType=1&gridViewStartDate=2017-07-19T07:00:00.000Z&gridViewEndDate=2017-07-25T07:00:00.000Z&gridViewSelectedDateRangeType=4)

Group D: 

- [Template to start an incident workflow](https://aka.ms/st-sre/training/d/sev3rangers)
- [Training On-Call List](https://icm.ad.msft.net/imp/v3/oncall/current?categoryId=0&serviceId=20592&teamIds=24825&scheduleType=timeline&shiftType=current&viewType=1&gridViewStartDate=2017-07-19T07:00:00.000Z&gridViewEndDate=2017-07-25T07:00:00.000Z&gridViewSelectedDateRangeType=4)

### Exercise:

#### Receiving a rangers alert and acknowledging the ticket

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

#### Assessing a Rangers ticket (Customer Support ticket)

Ranger's tickets are tickets that are customer specific or the negation is not a service outage. Sometimes a customer may experience custom issues that only pertain to them either one or two tenants or one or two users. The tier 1 team does not have to handle these there is a special team that will handle these in separate bridges. 

So how do we identify the customer support tickets:
1. They often start with "Online: ..." these are redirected customer support tickets
2. The title will always be freeform
3. Read through the description and see if it is only one customer (tenant or user)
4. See if the person creating the ticket has an alias starting with v-*, these could be testers accidentally filing bugs

What you should do now is transfer them to the rangers queue:
1. Click on the ticket
2. Click on the "Transfer" button
3. Service: Skype Teams
4. Teams: Rangers Followup
5. Any description of your reasoning is fine.

```Note: it is possible that they will return the ticket if it found to be customer reported livesite (global affect). This is common for issues involving Admin Portal Settings or other hard to monitor issues```

After you transfer the ticket is out of your scope.


