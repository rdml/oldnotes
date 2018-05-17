## What is it that I will do?

Assess: the situation by understand the impact, the severity and the scale of the incident

Identify: the issues and symptoms that are being experienced in the incident

Act: to mitigate the user symptoms experienced in the incident

Verify: that the mitigation was complete and that the incident is fully resolved

### Thousand Eyes (3rd Party External Probe)

Url is https://app.thousandeyes.com/dashboard/
Shared account is: sttheyes@microsoft.com / h2q7xicGUvGK9sQzTSz2
(NOTE: This is a "Regular User" account. To configure Thousand Eyes, please talk to one of the SREs)
Views -> Tests -> One of two Skype Teams tests (FE, MT)

Thousand Eyes is the tool to help you figure out if we are reaching out customers. Do you ever wonder how we detect if users can actually reach our site, resolve our DNS? Obviously if the user can't even hit our servers (network issues) we will never know. Not any more, Thousand Eyes is an external probing tool that has machines in standard ISP locations around the world. We have these machines ping our endpoints to make sure that all the networking stuff that is the internet is working correctly.

You can determine if:
```
- a probe is unable to find a route to one of our servers
- a particular country or region is facing major ISP network failures
- a DNS entry might not be resolvable in a region
- which region might be cut off
```

Hard to determine if:
```
- there are cert issues because the probing points are only http
- a network sever is with the ISP or internal Azure networks
- a problem machine issue or network issue
```

#### Viewing the probe history

![alt-text](https://domoreexp.visualstudio.com/DefaultCollection/11ac29bc-5a99-400b-b225-01839ab0c9df/_api/_versioncontrol/itemContent?repositoryId=e7e35b30-7782-4e79-a2fd-9f9bf23e1c0e&path=%2Ftsg%2Fimages%2Fthousandeyes_dashboard_view.png&version=GBlive&contentOnly=true&__v=5 "Thousand Eyes Dashboard Page")

You'll log in and start on the dashboard page. This page lists dashboards for all the tests we have in the system. The most important ones are the Frontend Webserver and the Middle Tier API server. The others can be relevant to your investigation as well. You can click on the test name to see the detailed "view" page. The at glance will also show you a rough graph of the timeline of the health probes so you can compare different tests quickly.

![alt-text](https://domoreexp.visualstudio.com/DefaultCollection/11ac29bc-5a99-400b-b225-01839ab0c9df/_api/_versioncontrol/itemContent?repositoryId=e7e35b30-7782-4e79-a2fd-9f9bf23e1c0e&path=%2Ftsg%2Fimages%2Fthousandeyes_test_timeline.png&version=GBlive&contentOnly=true&__v=5 "Example: Views page for Middletier Probing")

From the views page you can see the probing history as a timeline of the availability or you select individual times to see the impact on the global map. From the timeline, you'll be able to see the duration of the impact. Looking at the timeline you will want to assess how bad the situation is for the probes. Sometimes it is straight forward but sometimes the probes will see-saw a little bit between success and failure.

![alt-text](https://domoreexp.visualstudio.com/DefaultCollection/11ac29bc-5a99-400b-b225-01839ab0c9df/_api/_versioncontrol/itemContent?repositoryId=e7e35b30-7782-4e79-a2fd-9f9bf23e1c0e&path=%2Ftsg%2Fimages%2Fthousandeyes_test_map.png&version=GBlive&contentOnly=true&__v=5 "Example: A specific probe session showing issues with SSL in Hong Kong")

Next you need to click on some of the valleys in the timeline to look at the globla map. The global map will tell you specific probes that failed the test. If you see the same couple of probes failing for example, same 2 of 3 probes in the China and Japan then you can determine that there is a potential outage for that region. ```Act now: request a failover in that region``` If the cities are rotating around in a random pattern it could mean some other problem and not a localized outage.

Next you might always want to look at some of the other probe tests for other services. If these are showing the same pattern it means there is an ISP issue. ```Act now: request a failover in that region``` If these are not showing the same pattern it could be an Azure network issue because we use different Azure services that lie within different networks. If this is the case you should check the Azure health dashboard to see if there are any reported network problems. [Azure Health Status Dashboard](https://azure.microsoft.com/en-us/status/#current) ```Act now: escalate to Azure```

![alt-text](https://domoreexp.visualstudio.com/DefaultCollection/11ac29bc-5a99-400b-b225-01839ab0c9df/_api/_versioncontrol/itemContent?repositoryId=e7e35b30-7782-4e79-a2fd-9f9bf23e1c0e&path=%2Ftsg%2Fimages%2FAzure+status.png&version=GBlive&contentOnly=true&__v=5 "Azure Status Page")

```
What you should have learned:
- How to check if there are network issues reaching our main servers
- Check if there are regional network outages
- How to verify if it is an ISP or an Azure networking issue
- How to check the duration of the outage
- How to check which regions or cities are being impacted
```


