# Amazon Connect service quotas<a name="amazon-connect-service-limits"></a>

**All service quotas can be adjusted/increased unless otherwise noted\.**

Your AWS account has default quotas, formerly referred to as limits, for each AWS service\. 

To request a quota increase, see [Requesting a quota increase](https://docs.aws.amazon.com/servicequotas/latest/userguide/request-quota-increase.html) in the *Service Quotas User Guide*\. If the quota is not yet available in Service Quotas, use the [Amazon Connect service quotas increase form](https://console.aws.amazon.com/support/home#/case/create?issueType=service-limit-increase&limitType=service-code-connect)\. You must be signed in to your AWS account to access the form\.

**Topics**
+ [Important things to know](#important-quota-info)
+ [Amazon Connect quotas](#connect-quotas)
+ [AppIntegrations quotas](#app-integration-quotas)
+ [Cases quotas](#cases-quotas)
+ [Contact Lens quotas](#contactlens-quotas)
+ [Customer Profiles quotas](#customer-profiles-quotas)
+ [Outbound campaigns quotas](#outbound-communications-quotas)
+ [Voice ID quotas](#voiceid-quotas)
+ [Wisdom quotas](#wisdom-quotas)
+ [How contacts are counted](#contact-counting-criteria)
+ [Feature specifications](feature-limits.md)
+ [Countries you can call by default](country-code-allow-list.md)
+ [API throttling quotas](#api-throttling-quotas)

## Important things to know<a name="important-quota-info"></a>
+ You must create your instance before you can request a service quota increase\.
+ We review each request for a quota increase\. For smaller increase requests, we can approve in hours\. Larger increase requests take time to review, process, approve, and deploy\. Depending on your specific implementation, your resource, and the size of quota that you want, a request can take up to 3 weeks\. An extra\-large worldwide increase can potentially take months\. If you're increasing your quotas as part of a larger project, keep this information in mind and plan accordingly\.
+ Use the same form to submit a request to port your US phone number from your current carrier to Amazon Connect\. For more information about porting phone numbers, see [Port your current phone number to Amazon Connect](port-phone-number.md)\.
+ The quotas apply per [AWS Region](https://docs.aws.amazon.com/servicequotas/latest/userguide/intro.html#intro_getting-started)\. You can have multiple Amazon Connect instances in each Region\.  It's possible to raise quotas for all instances in a Region\.
+ This documentation describes the default quotas for new accounts\. Because the quotas have been adjusted over time, the default values for your account might be different than the default values described here\.

## Amazon Connect quotas<a name="connect-quotas"></a>


| Name | Default | Adjustable | 
| --- | --- | --- | 
|  AWS Lambda functions per instance  |  50  | No | 
|  Agent status per instance  |  50  | No | 
|  Amazon Connect instances per account  |  2  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-AA17A6B9) | 
|  Amazon Lex bots per instance  |  70  | No  | 
|  Amazon Lex V2 bot aliases per instance  |  100  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-12AB7C57)  | 
|  Concurrent active calls per instance   |  10 For more information, see [How contacts are counted](#contact-counting-criteria)\.  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-12AB7C57) | 
|  Concurrent active chats per instance  |  100 This includes chats that are waiting\. If this quota is exceeded, the API call fails with a quota exceeded error\.  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-D4BA6F6E) | 
|  Concurrent active tasks per instance  |  2500 concurrent active tasks All tasks that have not yet ended are considered active and are counted as concurrent tasks: tasks that are being routed in flows, waiting in a queue for an agent, being handled by agents, or being run in After Contact Work \(ACW\)\.   | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-60553137) | 
|  Flows per instance  |  100  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-22922690) | 
|  Hours of operation per instance  |  100  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-20CD02F7) | 
|  Maximum duration that a task can be scheduled in future  |  6 days  | No | 
|  Modules per instance  |  200  | No | 
|  Phone numbers per instance  |  5 It's possible to get an error message that "You've reached the limit of Phone Numbers," even if it's the first time you've claimed a phone number\. All the issues that cause this error message require help from AWS Support to resolve\.  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-8F812903) | 
|  Prompts per instance  |  500  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-0865B754) | 
|  Queues per instance  |  50  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-19A87C94) | 
|  Queues per routing profile per instance  |  50 This quota refers to number of queue/channel combinations per routing profile\. For example, in the following image there are two queues, but there are three queue\-channel combinations: Escalation queue Voice, Escalation queue Chat, and BasicQueue Voice\. This counts three towards the service limit of 50\. ![\[The Routing profiles page, the routing profiles queues section, voice and chat queues.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/routing-profile-queue-channel-combinations.png)  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-516BC0EB) | 
|  Quick connects per instance  |  100  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-68BBE2E8) | 
|  Rate of API requests  |  See [Amazon Connect API throttling quotas](#connect-api-quotas)\.  | Yes | 
|  Reports per instance  |  2000 Personal saved reports count towards the reports per instance\. For example, if one of your supervisors saves a report every day, it will count towards your overall number of saved reports per instance\. As a best practice, we recommend you implement policies so reports don't pile up\.   | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-79564E52) | 
|  Routing profiles per instance  |  100  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-D3E7BE26) | 
|  Scheduled reports per instance  |  50  | No | 
|  Security profiles per instance  |  100  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-F325A715) | 
|  Task templates per instance  |  50  | No | 
|  Task template customized fields per instance  |  50  | No | 
|  User hierarchy groups per instance  |  500 This quota applies to the total number of hierarchy groups you have, across all levels\. There is no feature limit for how many hierarchy groups you can have for each level\. For example, one level could have 500 hierarchy groups, which would reach the quota for your instance\.  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-D68AAAE4) | 
|  Users per instance  |  500  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-9A46857E) | 

## Amazon Connect AppIntegrations service quotas<a name="app-integration-quotas"></a>


| Name | Default | Adjustable | 
| --- | --- | --- | 
|  Data integration associations per data integration  |  10  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-6603B252) | 
|  Data integrations per Region  |  10  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-E3D2F503) | 
|  Event integration associations per event integration  |  10  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-3217D1F1) | 
|  Event integrations per Region  |  10  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-4A5ECB8E) | 

## Amazon Connect Cases service quotas<a name="cases-quotas"></a>


| Name | Default | Adjustable | 
| --- | --- | --- | 
|  Cases domains per AWS account  |  5  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-14092FF4) | 
|  Fields in a Cases domain  |  50  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-14092FF4) | 
|  Field options per single\-select field in the Cases domain  |  100  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-14092FF4) | 
|  Layouts in a Cases domain  |  25  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-14092FF4) | 
|  Templates in a Cases domain  |  25  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-14092FF4) | 
|  Related items that can be attached to a case  |  50  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-14092FF4) | 
|  Case fields per case template  |  30  | No | 

## Contact Lens service quotas<a name="contactlens-quotas"></a>


| Name | Default | Adjustable | 
| --- | --- | --- | 
|  Concurrent real\-time calls with analytics  |  50 100 for US East \(N\. Virginia\)  | Yes | 
|  Concurrent post\-call analytics jobs  |  200  See [Derive Concurrent post\-call analytics jobs based on your Amazon Connect call volume](#contactlens-concurrent-analytics-jobs)\.   | Yes | 
|  Concurrent post\-chat analytics jobs  |  200  | Yes | 

### Derive Concurrent post\-call analytics jobs based on your Amazon Connect call volume<a name="contactlens-concurrent-analytics-jobs"></a>

A post\-contact \(call or chat\) analytics job is kicked off after the completion of each contact with Contact Lens enabled\.  The time to complete a post\-contact analytics job is about 40% of the call length\. To calculate concurrent post\-call analytics jobs, use the following formula: 

`(average call duration in minutes) * (0.4) * (calls per hour) / (60)`

The following table shows some examples\.


| Average call duration \(in minutes\) | Calls per hour\* | Approximate Concurrent post\-call jobs | 
| --- | --- | --- | 
|  5  |  1000  | 33 | 
|  10  |  500  | 33 | 
|  10  |  1000  | 67 | 
|  10  |  3000  | 200 | 

\*For the calculations in the preceding table, we assume a fairly uniform distribution of calls during the hour\. If you have more complex traffic patterns, [contact AWS Support](https://console.aws.amazon.com/support/home) with details about your anticipated traffic pattern\.

## Amazon Connect Customer Profiles service quotas<a name="customer-profiles-quotas"></a>


| Name | Default | Adjustable | 
| --- | --- | --- | 
|  Amazon Connect Customer Profiles domains count  |  100  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-6603B252) | 
|  Keys per object type  |  10  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-E3D2F503) | 
|  Maximum expiration in days  |  1,096 \(3 years\) This is the expiration of objects and profiles\.  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-3217D1F1) | 
|  Maximum number of integrations  |  50  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-4A5ECB8E) | 
|  Maximum size of all objects for a profile  |  50MB  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-63975AF3) | 
|  Object and profile maximum size  |  250KB  | No | 
|  Object types per domain  |  100  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-14092FF4) | 
|  Objects per profile  |  1000 This is the maximum number of objects that can be attached to a profile\.  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect/quotas/L-E17DC7C3) | 
|  Maximum number of Identity Resolution Jobs each week for a domain  |  3  | No | 
|  Maximum number of consolidation rules in an Identity Resolution Job  |  10  | No | 
|  Maximum number of attributes in each consolidation rule  |  20  | No | 

## Outbound campaigns quotas<a name="outbound-communications-quotas"></a>


| Name | Default | Adjustable | 
| --- | --- | --- | 
|  Amazon Connect campaigns  |  25  | [Yes](https://console.aws.amazon.com/servicequotas/home/services/connect-campaigns/quotas/L-7F7B4C39) | 

## Amazon Connect Voice ID service quotas<a name="voiceid-quotas"></a>


| Item | Default quotas  | 
| --- | --- | 
|  Domains  |  3 This quota applies per account\.  | 
|  Concurrent active sessions per domain  |  50 See the following [table](#voiceid-concurrent-active-sessions) for information about how to derive your **Concurrent active sessions** quota based on your Amazon Connect call volume\.  | 
|  Maximum number of fraudsters per watchlist  |  500  | 
|  Maximum number of watchlists per domain  |  3, including the default watchlist of a domain  | 
|  Maximum number of speakers per domain  |  100,000  | 
|  Active Batch Speaker Enrollment Jobs per domain  |  1  | 
|  Active Batch Fraudster Registration Jobs per domain  |  1  | 
|  Speakers per Batch Speaker Enrollment Job  |  10,000  | 
|  Fraudsters per Batch Fraudster Registration Job  |  500  | 

### Derive Concurrent active sessions based on your Amazon Connect call volume<a name="voiceid-concurrent-active-sessions"></a>

Use the information in the following table to derive your quota for Voice ID **Concurrent active sessions per domain**\. Base your quota on the number of voice calls handled by your Amazon Connect contact center where Voice ID is enabled\.


| Amazon Connect Voice Contacts \(Calls\)/Hour\* | Voice ID Concurrent active sessions | 
| --- | --- | 
|  1,000  |  50  | 
|  5,000  |  250  | 
|  10,000  |  500  | 
|  20,000  |  1,000  | 
|  50,000  |  2,500  | 

\*For the calculations in the preceding table, we assume a fairly uniform distribution of calls during the hour\. If you have more complex traffic patterns, [contact AWS Support](https://console.aws.amazon.com/support/home) with details about your anticipated traffic pattern\.

## Amazon Connect Wisdom service quotas<a name="wisdom-quotas"></a>


| Item | Default quotas  | Adjustable | 
| --- | --- | --- | 
|  Assistants  |  5  | No | 
|  Knowledge bases  |  10  | 
|  Maximum size of a knowledge base  |  5GB per knowledge base  | 
|  Content per knowledge base  |  5,000 Examples of content are frequently asked questions \(FAQs\), wikis, articles, and step\-by\-step instructions for handling different customer issues\.  | 
|  Maximum size per document  |  1MB  | 
|  RateLimit for all APIs  |  50TPS  | 

## How contacts are counted<a name="contact-counting-criteria"></a>

The following contacts are counted in **Concurrent active calls per instance**:
+ Handled by a flow
+ Waiting in queue
+ Handled by an agent
+ Outbound call

The following contacts are not counted:
+ Callbacks waiting in a callback queue are not counted until the callback is offered to an available agent\.
+ External transfers

If the quota for **Concurrent active calls per instance** is exceeded, contacts get a reorder tone \(also known as a fast busy tone\), which indicates that there is no available transmission path to the called number\.

You can calculate your configured quota using CloudWatch metrics\. For instructions, see [Use CloudWatch metrics to calculate concurrent call quota](monitoring-cloudwatch.md#connect-cloudwatch-concurrent-call-quota)\. 

If you're only taking calls you can also determine your **Concurrent active calls per instance** quota by doing the following:

1. Navigate to the **Edit a queue** page: choose **Routing**, **Queues**, and choose a queue\.

1. Choose **Set a limit across all channels**\. 

1. Enter an exceptionally large number in the **Maximum contacts in queue** box for the contact limit\.

The resulting error message displays your quota as **Concurrent active calls per instance** \- 1\. 

For example, in the following image from the **Edit queues** page, you add 1 to the error message, to get **Concurrent active calls per instance** quota = 10\.

![\[The edit queue page, Maximum contacts in queue set to 1000, a message that max contacts is 9.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/concurrent-call-quota.png)

The error message shows 9 because you must set always set **Maximum contacts in queue** to a number that is at least 1 *less than* your **Concurrent active calls per instance** quota \(which is the default limit\)\.

## API throttling quotas<a name="api-throttling-quotas"></a>

### Amazon Connect API throttling quotas<a name="connect-api-quotas"></a>

Amazon Connect throttling quotas are by account, and per Region, not by user and not by instance\. For example: 
+ If different users from the same account make requests, they are sharing a throttle bucket\. 
+ If multiple requests are sent from different instances from the same account, they are also sharing a throttle bucket\. 

 When you use the [Amazon Connect Service API ](https://docs.aws.amazon.com/connect/latest/APIReference/welcome.html), the number of requests per second is limited to the following:
+ For the [GetMetricData ](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricData.html) and [GetCurrentMetricData ](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetCurrentMetricData.html) operations, a RateLimit of 5 requests per second, and a BurstLimit of 8 requests per second\.
**Note**  
The rate limit cannot be increased for GetMetricData and GetCurrentMetricData\.
+ For [StartChatContact](https://docs.aws.amazon.com/connect/latest/APIReference/API_StartChatContact.html), [StartContactStreaming](https://docs.aws.amazon.com/connect/latest/APIReference/API_StartContactStreaming.html), [StopContactStreaming](https://docs.aws.amazon.com/connect/latest/APIReference/API_StopContactStreaming.html), a RateLimit of 5 requests per second, and a BurstLimit of 8 requests per second\.
+ For all other operations, a RateLimit of 2 requests per second, and a BurstLimit of 5 requests per second\.

### Amazon Connect Participant Service API throttling quotas<a name="connect-participant-api-quotas"></a>

For the Amazon Connect Participant Service, the quotas are by instance\.

 When you use the [Amazon Connect Participant Service API](https://docs.aws.amazon.com/connect-participant/latest/APIReference/Welcome.html), the number of requests per second is limited to the following:
+  [CreateParticipantConnection](https://docs.aws.amazon.com/connect/latest/APIReference/API_CreateParticipantConnection.html): a RateLimit of 6 requests per second, and a BurstLimit of 9 requests per second\.
+  [DisconnectParticipant](https://docs.aws.amazon.com/connect/latest/APIReference/API_DisconnectParticipant.html): a RateLimit of 3 requests per second, and a BurstLimit of 5 requests per second\.
+  [GetTranscript](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetTranscript.html): a RateLimit of 8 requests per second, and a BurstLimit of 12 requests per second\.
+  [SendEvent](https://docs.aws.amazon.com/connect/latest/APIReference/API_SendEvent.html) and [SendMessage](https://docs.aws.amazon.com/connect/latest/APIReference/API_SendMessage.html): a RateLimit of 10 requests per second, and a BurstLimit of 15 requests per second\.
+  [StartAttachmentUpload](https://docs.aws.amazon.com/connect/latest/APIReference/API_StartAttachmentUpload.html): a RateLimit of 2 requests per second, and a BurstLimit of 5 requests per second\.
+  [CompleteAttachmentUpload](https://docs.aws.amazon.com/connect/latest/APIReference/API_CompleteAttachmentUpload.html): a RateLimit of 2 requests per second, and a BurstLimit of 5 requests per second\.
+  [GetAttachment](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetAttachment.html): a RateLimit of 8 requests per second, and a BurstLimit of 12 requests per second\.

### Amazon Connect Contact Lens Service API throttling quotas<a name="connect-contactlens-api-quotas"></a>

Amazon Connect Contact Lens throttling quotas are by account, not by user and not by instance\. For example:
+ If different users from the same account make requests, they are sharing a throttle bucket\.
+ If multiple requests are sent from different instances from the same account, they are also sharing a throttle bucket\. 

When you use the [Amazon Connect Contact Lens API](https://docs.aws.amazon.com/contact-lens/latest/APIReference/Welcome.html), the number of requests per second is limited to the following:
+ [ListRealtimeContactAnalysisSegments](https://docs.aws.amazon.com/contact-lens/latest/APIReference/ListRealtimeContactAnalysisSegments.html): a RateLimit of 1 request per second, and a BurstLimit of 2 requests per second\.

### Amazon Connect Cases API throttling quotas<a name="cases-api-quotas"></a>


| API | Default TPS throttling limits | 
| --- | --- | 
|  CreateCase, SearchCases, UpdateCase, AssociateContact, ListTemplates, CreateRelatedItem, SearchRelatedItems  |  10  | 
|  CreateField, ListFields, CreateDomain, GetDomain,CreateTemplate, BatchPutFieldOptions, CreateLayout, UpdateLayout, UpdateTemplate, UpdateField  |  5  | 
|  BatchGetField  |  25  | 
|  GetCase  |  15  | 
|  GetTemplate, GetLayout  |  20  | 
|  ListFieldOptions  |  15  | 

### Amazon Connect Voice ID Service API throttling quotas<a name="voiceid-api-quotas"></a>


| API | Default TPS throttling limits | 
| --- | --- | 
|  EvaluateSession  |  60  | 
|  Domain APIs: CreateDomain, DescribeDomain, UpdateDomain, DeleteDomain, ListDomains Batch APIs: StartSpeakerEnrollmentJob, DescribeSpeakerEnrollmentJob, ListSpeakerEnrollmentJobs, StartFraudsterRegistrationJob, DescribeFraudsterRegistrationJob, ListFraudsterRegistrationJobs  |  2  | 
|  ListSpeakers  |  5  | 
|  DescribeSpeaker, OptOutSpeaker, DeleteSpeaker, DescribeFraudster, DeleteFraudster  |  10  | 
|  CreateIntegrationAssociation, DeleteIntegrationAssociation, ListIntegrationAssociation  |  2  | 
|  TagResource, UnTagResource, ListTagsForResource  |  2  | 