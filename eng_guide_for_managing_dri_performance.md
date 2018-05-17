## What is it that I will do?

Assess: the situation by understand the impact, the severity and the scale of the incident

Identify: the issues and symptoms that are being experienced in the incident

Act: to mitigate the user symptoms experienced in the incident

Verify: that the mitigation was complete and that the incident is fully resolved

### Being the operations manager

As the operations manager, you're roll is to make sure that you are the eyes and ears of the livesite. To do this we manage the different tier 2 DRI from our dashboards. The goal of this role is to make sure we don't have blindspots that week due to newly added code/monitors or weaknesses due to DRI performance. Its a very passive role that just requires you to be aware of the situation.

#### Are Tier 2 DRI checking their queues

The reality is that most tier 2 DRI are good at responding when there are phone calls. But its all the other homework that kind of gets skipped over.

This first dashboard shows the tickets that are active and unacknowledged. The core take away from this dashboard are:
1. Are some teams addressing the tickets they have? (too many tickets, threshold is about 20 per team, 10 per DRI)
2. Are the tickets being acknowledged? (too many unacknowledged tickets, this number should always be low)
3. Are there any sev 1 or sev 2 tickets that are unacknowledged? (you do not want any of these to go unacknowledge at all)
4. Are there a lot of sev 1 or sev 2 tickets? (this usually indicates that that team needs more help and they are being overwelmed, or the whole org needs more cross team work on livesites)

[Team Duty Performance](https://msit.powerbi.com/groups/bd8714db-51c2-43af-9f11-8b3d05fb67da/reports/1f82a134-a8d0-4549-8a57-e017ed1d902f/ReportSection9)

![alt-text](https://domoreexp.visualstudio.com/DefaultCollection/11ac29bc-5a99-400b-b225-01839ab0c9df/_api/_versioncontrol/itemContent?repositoryId=e7e35b30-7782-4e79-a2fd-9f9bf23e1c0e&path=%2Fsre_guides%2Fimages%2Fdashboard_activetickets.png&version=GBlive&contentOnly=true&__v=5 "Teams DRI Duty Performance")

**How to address these issues**

```
1. Go into the team "Microsoft Teams" and channel "Livesite"
2. Create a new thread titled "XXX DRI on-call duty needs addressing"
3. Add a link to https://aka.ms/st-sre/operations
4. Add a screenshot of the current page (so you have something to compare with after they clean up)
5. At mention, GEM, EMs, primary and secondary on-call for the team [https://aka.ms/st-sre/tier2](https://aka.ms/st-sre/tier2)
6. Indicate in text what their problem is.
7. At mention, Scott Grosenick, Lawrence Chan, Spoorthi Gururaj, Dan Massey
```

#### Are Tier 2 queues getting tickets from other sources

This is an operations concern because if there are too many manual tickets to a team or too many security tickets we want to know about them and we should quickly bring it to the SRE attention.

This dashboard shows the tickets source. A legend of the different sources are:
- Build-Infra-ICMTool - this is the build break, ICM tool owned by Build team
- ExpiringCertAlert - this is a common source of failure because it comes in as low priority
- ICMPortal - 


The core take away from this dashboard are:
1. Are some teams addressing the tickets they have? (too many tickets, threshold is about 20 per team, 10 per DRI)
2. Are the tickets being acknowledged? (too many unacknowledged tickets, this number should always be low)
3. Are there any sev 1 or sev 2 tickets that are unacknowledged? (you do not want any of these to go unacknowledge at all)
4. Are there a lot of sev 1 or sev 2 tickets? (this usually indicates that that team needs more help and they are being overwelmed, or the whole org needs more cross team work on livesites)

[Team Auto-Detect Performance](https://msit.powerbi.com/groups/bd8714db-51c2-43af-9f11-8b3d05fb67da/reports/1f82a134-a8d0-4549-8a57-e017ed1d902f/ReportSection10)

![alt-text](https://domoreexp.visualstudio.com/DefaultCollection/11ac29bc-5a99-400b-b225-01839ab0c9df/_api/_versioncontrol/itemContent?repositoryId=e7e35b30-7782-4e79-a2fd-9f9bf23e1c0e&path=%2Fsre_guides%2Fimages%2Fdashboard_autodetect.png&version=GBlive&contentOnly=true&__v=5)

**How to address these issues**

```
1. Go into the team "Microsoft Teams" and channel "Livesite"
2. Create a new thread titled "XXX DRI on-call duty needs addressing"
3. Add a link to https://aka.ms/st-sre/operations
4. Add a screenshot of the current page (so you have something to compare with after they clean up)
5. At mention, GEM, EMs, primary and secondary on-call for the team [https://aka.ms/st-sre/tier2](https://aka.ms/st-sre/tier2)
6. Indicate in text what their problem is.
7. At mention, Scott Grosenick, Lawrence Chan, Spoorthi Gururaj, Dan Massey
```

#### Are Tier 2 dealing with their tickets in a timely fashion

This is an operations concern because this dashboard shows the accumulated time of tickets that haven't been mitigated. It is not common knowledge for DRIs that they need to acknowledge all tickets in 2h (either 24x7 or office hours). Its also not ok to keep letting tickets sit unmitigated. These charts help you point out teams that have been neglecting their livesites.

This dashboard shows negative action on mitigating tickets. 
1. [top-left]: Shows the accumulated days of tickets that are unmitigated. So its Sum of all tickets (Sum of days since created and still active tickets))
2. [top-right]: Shows the number of tickets per team and is a good way to value the top-left chart. A team with a high value of days and low count of tickets indicates no one is mitigating their tickets.
3. [bottom-left]: Shows the worst ticket by day for each team and severity. Values close to 30 indicate tickets are being ignored.
4. [bottom-right]: Shows the tickets that are mitigated by not resolved. This tells you to follow up on folks because this usually indicates that a post mortem was skipped.

The core take away from this dashboard are:
1. Is a team DRI not looking at their tickets?
2. Is a team leaving some tickets unmitigated or ignoring them?
3. Is the ignoring chronic, because their worst tickets are over 20 days?
4. Are teams missing post mortems because their ticket is mitigated but not resolved?
5. Are teams having reoccurring incidents because tickets are remaining mitigated for a long time.

[Team Mitigation Performance](https://msit.powerbi.com/groups/bd8714db-51c2-43af-9f11-8b3d05fb67da/reports/1f82a134-a8d0-4549-8a57-e017ed1d902f/ReportSection)

![alt-text](https://domoreexp.visualstudio.com/DefaultCollection/11ac29bc-5a99-400b-b225-01839ab0c9df/_api/_versioncontrol/itemContent?repositoryId=e7e35b30-7782-4e79-a2fd-9f9bf23e1c0e&path=%2Fsre_guides%2Fimages%2Fdashboard_mitigationbyteam.png&version=GBlive&contentOnly=true&__v=5)

**How to address these issues**

```
1. Go into the team "Microsoft Teams" and channel "Livesite"
2. Create a new thread titled "XXX DRI on-call duty needs to mitigate and resolve their tickets"
3. Add a link to https://aka.ms/st-sre/operations
4. Add a screenshot of the current page (so you have something to compare with after they clean up)
5. At mention, GEM, EMs, primary and secondary on-call for the team [https://aka.ms/st-sre/tier2](https://aka.ms/st-sre/tier2)
6. Indicate in text what their problem is.
7. At mention, Scott Grosenick, Lawrence Chan, Spoorthi Gururaj, Dan Massey
```

#### Are Tier 2 queues dealing with phone calls

This is an operations concern because it is not ideal that teams might be getting too many phone calls. Its a sign their service has some issues or that they have underlying issues to look into.

This dashboard shows the phone calls and notifications 
1. [top-left]: Shows calls made per team, it breaks down into ones from tickets vs request assistance calls.
2. [bottom-left]: Shows the notifications by email that were made, the severity of these tickets were too low to trigger a phone call. If your team is getting a lot of these it might mean the severity is wrong or the monitoring needs improvement.
3. [top-right]: Shows the total silent and phone call based notifications sent by team. This is an aggregated view ignoring that some notifications would not get immediate attention.
4. [bottom-right]: Shows the source of the notification, these are broken down into: ticket severity change, transfer, request assistance and initial ticket creation.

The core take away from this dashboard are:
1. Is a team getting too many phone calls?
2. Is a team getting a lot of silent notifications that might be missed?
3. Is a team getting R/A a lot so that maybe the target of tickets is going to the wrong team?
4. Are a teams alerts working well?
5. Does a team need to start using more correlation rules?

[Team Phone Calls/Notification Performance](https://msit.powerbi.com/groups/bd8714db-51c2-43af-9f11-8b3d05fb67da/reports/1f82a134-a8d0-4549-8a57-e017ed1d902f/ReportSection1)

![alt-text](https://domoreexp.visualstudio.com/DefaultCollection/11ac29bc-5a99-400b-b225-01839ab0c9df/_api/_versioncontrol/itemContent?repositoryId=e7e35b30-7782-4e79-a2fd-9f9bf23e1c0e&path=%2Fsre_guides%2Fimages%2Fdashboard_phonecalls.png&version=GBlive&contentOnly=true&__v=5)

**How to address these issues**

```
1. Go into the team "Microsoft Teams" and channel "Livesite"
2. Create a new thread titled "XXX DRI on-call duty should check on their request assistance and phone call rate"
3. Add a link to https://aka.ms/st-sre/operations
4. Add a screenshot of the current page (so you have something to compare with after they clean up)
5. At mention, GEM, EMs, primary and secondary on-call for the team [https://aka.ms/st-sre/tier2](https://aka.ms/st-sre/tier2)
6. Indicate in text what their problem is.
7. At mention, Scott Grosenick, Lawrence Chan, Spoorthi Gururaj, Dan Massey
```

#### Are Tier 2 teams transfer tickets and partners response rate

This is an operations concern because if teams are transfering tickets to partner teams we need to make sure they are still being looked at.

This dashboard shows the phone calls and notifications 
1. [top-left]: Shows total days of unmitigated tickets by partner team.
2. [bottom-left]: Shows the worse ticket with unmitigated days by partner team.
3. [top-right]: Shows the incident count by partner team
4. [bottom-right]: Shows the mitigated by not resolved tickets by partner team

The core take away from this dashboard are:
1. Is a team DRI not looking at their tickets?
2. Is a team leaving some tickets unmitigated or ignoring them?
3. Is the ignoring chronic, because their worst tickets are over 20 days?
4. Are teams missing post mortems because their ticket is mitigated but not resolved?
5. Are teams having reoccurring incidents because tickets are remaining mitigated for a long time.

[Partner Team Mitigation Performance](https://msit.powerbi.com/groups/bd8714db-51c2-43af-9f11-8b3d05fb67da/reports/1f82a134-a8d0-4549-8a57-e017ed1d902f/ReportSection3830dac6264982abd403)

![alt-text](https://domoreexp.visualstudio.com/DefaultCollection/11ac29bc-5a99-400b-b225-01839ab0c9df/_api/_versioncontrol/itemContent?repositoryId=e7e35b30-7782-4e79-a2fd-9f9bf23e1c0e&path=%2Fsre_guides%2Fimages%2Fdashboard_partnermitigationbyteam.png&version=GBlive&contentOnly=true&__v=5)

**How to address these issues**

```
1. Go into the team "Microsoft Teams" and channel "Livesite"
2. Create a new thread titled "XXX DRI on-call duty should follow up with partners to action on their ICM tickets"
3. Add a link to https://aka.ms/st-sre/operations
4. Add a screenshot of the current page (so you have something to compare with after they clean up)
5. At mention, GEM, EMs, primary and secondary on-call for the team [https://aka.ms/st-sre/tier2](https://aka.ms/st-sre/tier2)
6. Indicate in text what their problem is.
7. At mention, Scott Grosenick, Lawrence Chan, Spoorthi Gururaj, Dan Massey
```