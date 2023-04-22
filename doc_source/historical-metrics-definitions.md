# Historical metrics definitions<a name="historical-metrics-definitions"></a>

The following metrics are available to include in historical metrics reports in Amazon Connect\.

**Tip**  
Developers can use the [GetMetricData](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricData.html) and [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) APIs to get a subset of the following historical metrics from the specified Amazon Connect instance\.

## Adherence<a name="adherence-historical"></a>

This metric is available only in AWS Regions where [Forecasting, capacity planning, and scheduling](regions.md#optimization_region) is available\.

The percentage of time that an agent correctly follows their schedule\. This is measured by tracking if an agent is in an *Available* agent status when they should be in productive state\. This percentage is calculated as follows: 

Adherence % = \(\(Total Adherent Minutes\)/ Total Scheduled Adherence Minutes\)

An agent is considered adherent if the agent is in an *Available* status, when the shift activity is *Productive*, or if the agent is in *Non\-Productive* status \(for example, a custom status\), when the shift activity is Non\-Productive\. Otherwise the agent is considered non\-adherent\. This means that if a shift activity is named *Lunch* but marked as productive, the agent is considered adherent if they are in the *Available* agent status\.

In the [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) API, this metric is `AGENT_SCHEDULE_ADHERENCE`\.

Type: String

Min value: 0\.00%

Max value: 100\.00%

Category: Agent activity\-driven metric

**Note**  
Any time you change the schedule, Schedule Adherence is re\-calculated up to 30 days in the past from the current date \(not the date of the schedule\), if schedules are changed\.

## Adherent time<a name="adherent-time-historical"></a>

This metric is available only in AWS Regions where [Forecasting, capacity planning, and scheduling](regions.md#optimization_region) is available\.

The total time an agent was in an *Available* status when their shift activity is productive or was is in non\-productive status when the shift activity is non\-productive\.

In the [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) API, this metric is `AGENT_ADHERENT_TIME`\.

Type: String

Category: Agent activity\-driven metric

## After contact work time<a name="acw-historical"></a>

The total time that an agent spent doing ACW for a contact\. In some businesses, also known as Call Wrap Up time\.  

You specify the amount of time an agent has to do ACW in their [ agent configuration settings](configure-agents.md)\. When a conversation with a contact ends, the agent is automatically allocated to do ACW for the contact\. They stop doing ACW for a contact when they indicate they are ready for another contact in the CCP\.

In the [GetMetricData](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricData.html) API, this metric is `AFTER_CONTACT_WORK_TIME`\.

Type: String \(*hh:mm:ss*\)

Category: contact record\-driven metric

## Agent answer rate<a name="agent-answer-rate-historical"></a>

Percentage of contacts routed to an agent that were answered\.

Type: String 

Min value: 0\.00%

Max value: 100\.00%

Category: Agent activity\-driven metric

## Agent API connecting time<a name="htm-agent-api-connecting-time"></a>

The total time between when a contact is initiated using an Amazon Connect API, and the agent is connected\.

Type: String \(hh:mm:ss\)

Category: Agent activity\-driven metric

## Agent callback connecting time<a name="htm-agent-callback-connecting-time"></a>

The total time between when a callback contact is initiated by Amazon Connect reserving the agent for the contact, and the agent is connected\.

Type: String \(hh:mm:ss\)

Category: Agent activity\-driven metric

## Agent first name<a name="agent-first-name-historical"></a>

The first name of the agent, as entered in their Amazon Connect user account\. This metric is available only when grouping by agent\.

Type: String 

Length: 1\-255

## Agent idle time<a name="agent-idle-time-historical"></a>

After the agent sets their status in the CCP to **Available**, this is the amount of time they weren't handling contacts \+ any time their contacts were in an Error state\. 

Agent idle time doesn’t include the amount of time from when Amazon Connect starts routing the contact to the agent, to when agent picks up or declines the contact\.

Type: String \(*hh:mm:ss*\)

Category: Agent activity\-driven metric

## Agent incoming connecting time<a name="htm-agent-incoming-connecting-time"></a>

The total time between when a contact is initiated by Amazon Connect reserving the agent for the contact, and the agent is connected\.

In the agent event stream, this is the duration between the contact state of STATE\_CHANGE event changes from CONNECTING to CONNECTED/MISSED/ERROR\. 

Type: String \(hh:mm:ss\)

Category: Agent activity\-driven metric

## Agent interaction and hold time<a name="agent-interaction-hold-time-historical"></a>

Sum of [Agent interaction time](#agent-interaction-time-historical) and [Customer hold time](#customer-hold-time-historical)\.

Type: String \(*hh:mm:ss*\)

Category: contact record\-driven metric

## Agent interaction time<a name="agent-interaction-time-historical"></a>

Total time that agents spent interacting with customers on inbound and outbound contacts\. This does not include [Customer Hold Time](#customer-hold-time-historical) or [After Contact Work Time](#acw-historical)\.

Type: String \(*hh:mm:ss*\)

Category: contact record\-driven metric

## Agent last name<a name="agent-last-name-historical"></a>

The last name of the agent, as entered in their Amazon Connect user account\. This metric is available only when grouping by agent\.

Type: String 

Length: 1\-255

## Agent name<a name="agent-name-historical"></a>

The name of the agent, displayed as follows: **Agent last name**, **Agent first name**\. This metric is available only when grouping by agent\.

## Agent non\-response<a name="agent-non-response"></a>

Count of contacts routed to an agent but not answered by that agent, including contacts abandoned by the customer\. 

If a contact is not answered by a given agent, we attempt to route it to another agent to handle; the contact is not dropped\. Because a single contact can be missed multiple times \(including by the same agent\), it can be counted multiple times: once for each time it is routed to an agent but not answered\.

This metric appears as **Contacts missed** in scheduled reports and exported CSV files\.

Type: Integer 

Category: Agent activity\-driven metric

## Agent on contact time<a name="agent-on-contact-time-historical"></a>

Total time that an agent spent on a contact, including [Customer Hold Time](#customer-hold-time-historical) and [After Contact Work Time](#acw-historical)\. This does **not** include time spent on a contact while in a custom status or **Offline** status\. \(Custom status = the agent's CCP status is other than **Available** or **Offline**\. For example, Training would be a custom status\.\)

**Tip**  
If you want to include the time spent in a custom status and **Offline** status, see [Contact handle time](#contact-handle-time-historical)\.

Type: String \(*hh:mm:ss*\)

Category: Agent activity\-driven metric

## Agent outbound connecting time<a name="htm-agent-outbound-connecting-time"></a>

Total time between when an outbound contact is initiated by Amazon Connect reserving the agent for the contact, and the agent is connected\.

Type: String \(hh:mm:ss\)

Category: Agent activity\-driven metric

## API contacts<a name="api-contacts-historical"></a>

Count of contacts that were initiated using an Amazon Connect API operation, such as `StartOutboundVoiceContact`\. This includes contacts that were not handled by an agent\.

Type: Integer 

Category: contact record\-driven metric

## API contacts handled<a name="api-contacts-handled-historical"></a>

Count of contacts that were initiated using an Amazon Connect API operation, such as `StartOutboundVoiceContact`, and handled by an agent\.

In the [GetMetricData](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricData.html) API, this metric is `API_CONTACTS_HANDLED`\.

In the [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) API, this metric can be retrieved by using `CONTACTS_HANDLED` with a [MetricFilters](https://docs.aws.amazon.com/connect/latest/APIReference/API_MetricV2.html) parameter set as follows:
+ `MetricFilterKey` = `INITIATION_METHOD`
+ `MetricFilterValues` = `API`

Type: Integer 

Category: contact record\-driven metric

## Average after contact work time<a name="average-acw-time-historical"></a>

Average amount of time that an agent spent doing After Contact Work \(ACW\) for contacts\. This is calculated by averaging [AfterContactWorkDuration](ctr-data-model.md#AfterContactWorkDuration-CTR) \(from the contact record\) for all contacts included in the report, based on the selected filters\.

In the [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) API, this metric is `AVG_AFTER_CONTACT_WORK_TIME`\.

Type: String \(*hh:mm:ss*\)

Category: contact record\-driven metric

## Average agent API connecting time<a name="htm-avg-agent-api-connecting-time"></a>

The average time between when a contact is initiated using an Amazon Connect API, and the agent is connected\. 

In the [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) API, this metric can be retrieved by using `AVG_AGENT_CONNECTING_TIME` with a [MetricFilters](https://docs.aws.amazon.com/connect/latest/APIReference/API_MetricV2.html) parameter set as follows:
+ `MetricFilterKey` = `INITIATION_METHOD`
+ `MetricFilterValues` = `API`

Type: String \(hh:mm:ss\)

Category: Agent activity\-driven metric

## Average agent callback connecting time<a name="htm-avg-agent-callback-connecting-time"></a>

The average time between when a callback contact is initiated by Amazon Connect reserving the agent for the contact, and the agent is connected\. 

In the [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) API, this metric can be retrieved by using `AVG_AGENT_CONNECTING_TIME` with a [MetricFilters](https://docs.aws.amazon.com/connect/latest/APIReference/API_MetricV2.html) parameter set as follows:
+ `MetricFilterKey` = `INITIATION_METHOD`
+ `MetricFilterValues` = `CALLBACK`

Type: String \(hh:mm:ss\)

Category: Agent activity\-driven metric

## Average agent incoming connecting time<a name="htm-avg-agent-incoming-connecting-time"></a>

The average time between when contact is initiated by Amazon Connect reserving the agent for the contact, and the agent is connected\. This is the ring time for configurations where the agent is not set to auto\-answer\.

No equivalent to this metric is available in the `GetMetricData` API\. 

In the [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) API, this metric can be retrieved by using `AVG_AGENT_CONNECTING_TIME` with a [MetricFilters](https://docs.aws.amazon.com/connect/latest/APIReference/API_MetricV2.html) parameter set as follows:
+ `MetricFilterKey` = `INITIATION_METHOD`
+ `MetricFilterValues` = `INBOUND`

Type: String \(hh:mm:ss\)

Category: Agent activity\-driven metric

## Average agent interaction and customer hold time<a name="average-agent-interaction-customer-hold-time-historical"></a>

Average of the sum of the agent interaction and customer hold time\. This is calculated by averaging the sum of the following values from the contact record: [AgentInteractionDuration](ctr-data-model.md#AgentInteractionDuration-CTR) and [CustomerHoldDuration](ctr-data-model.md#CustomerHoldDuration-CTR)\.

In the [GetMetricData](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricData.html) API, this metric is `INTERACTION_AND_HOLD_TIME`\.

In the [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) API, this metric is `AVG_INTERACTION_AND_HOLD_TIME`\.

Type: String \(*hh:mm:ss*\)

Category: contact record\-driven metric

## Average agent interaction time<a name="average-agent-interaction-time-historical"></a>

Average time that agents interacted with customers during inbound and outbound contacts\. This does not include [Customer Hold Time](#customer-hold-time-historical) or [After Contact Work Time](#acw-historical)\.

In the [GetMetricData](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricData.html) API, this metric is `INTERACTION_TIME`\.

In the [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) API, this metric is `AVG_INTERACTION_TIME`\.

Type: String \(*hh:mm:ss*\)

Category: contact record\-driven metric

## Average agent outbound connecting time<a name="htm-avg-agent-outbound-connecting-time"></a>

The average time between when an outbound contact is initiated by Amazon Connect reserving the agent for the contact, and the agent is connected\. 

In the [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) API, this metric can be retrieved by using `AVG_AGENT_CONNECTING_TIME` with a [MetricFilters](https://docs.aws.amazon.com/connect/latest/APIReference/API_MetricV2.html) parameter set as follows:
+ `MetricFilterKey` = `INITIATION_METHOD`
+ `MetricFilterValues` = `OUTBOUND`

Type: String \(hh:mm:ss\)

Category: Agent activity\-driven metric

## Average customer hold time<a name="average-customer-hold-time-historical"></a>

Average time that customers spent on hold while connected to an agent\. This is calculated by averaging [CustomerHoldDuration](ctr-data-model.md#CustomerHoldDuration-CTR) \(from the contact record\)\.

In the [GetMetricData](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricData.html) API, this metric is `HOLD_TIME`\.

In the [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) API, this metric is `AVG_HOLD_TIME`\.

This average only includes contacts that went on hold\.

Type: String \(*hh:mm:ss*\)

Category: contact record\-driven metric

This metric doesn't apply to tasks so you'll notice a value of 0 on the report for them\.

## Average handle time<a name="average-handle-time-historical"></a>

The average time, from start to finish, that a contact was connected with an agent \(average handled time\)\. It includes talk time, hold time, and After Contact Work \(ACW\) time\.

AHT is calculated by averaging the amount of time between the contact being answered by an agent and the conversation ending\. It applies to both inbound and outbound calls\.

AHT is different from [Contact handle time](#contact-handle-time-historical)\. AHT does not include any time spent in a custom status; Contact handle time \(CHT\) does include it\.

In the [GetMetricData](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricData.html) API, this metric is `HANDLE_TIME`\.

In the [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) API, this metric is `AVG_HANDLE_TIME`\.

Type: String \(*hh:mm:ss*\)

Category: contact record\-driven metric

## Average outbound after contact work time<a name="average-outbound-acw-time-historical"></a>

Average time that agents spent doing After Contact Work \(ACW\) for an outbound contact\.

Type: String \(*hh:mm:ss*\)

Category: contact record\-driven metric

## Average outbound agent interaction time<a name="average-outbound-agent-interaction-time-historical"></a>

Average time that agents spent interacting with a customer during an outbound contact\.

Type: String \(*hh:mm:ss*\)

Category: contact record\-driven metric

## Average queue abandon time<a name="average-queue-abandon-time-historical"></a>

Average time that contacts waited in the queue before being abandoned\. This is calculated by averaging the difference between [EnqueueTimestamp](ctr-data-model.md#EnqueueTimestamp-CTR) and [DequeueTimestamp](ctr-data-model.md#DequeueTimestamp-CTR) \(from the contact record\) for abandoned contacts\. 

A contact is considered abandoned if it was removed from a queue but not answered by an agent or queued for callback\.

In the [GetMetricData](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricData.html) API, this metric is ABANDON\_TIME\.

In the [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) API, this metric is `AVG_ABANDON_TIME`\.

Type: String \(*hh:mm:ss*\)

Category: contact record\-driven metric

## Average queue answer time<a name="average-queue-answer-time-historical"></a>

Average time that contacts waited in the queue before being answered by an agent\. In some businesses, this is also known as average speed of answer \(ASA\)\.

Average queue answer time also includes the time during the agent whisper, because the contact remains in queue until the agent whisper is completed\. 

This is the average of [Duration](ctr-data-model.md#Duration-CTR) \(from the contact record\)\.

In the [GetMetricData](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricData.html) API, this metric is `QUEUE_ANSWER_TIME`\.

In the [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) API, this metric is `AVG_QUEUE_ANSWER_TIME`\.

Type: String \(*hh:mm:ss*\)

Category: contact record\-driven metric

## Callback attempts<a name="callback-attempts-historical"></a>

The number of contacts where a callback was attempted, but the customer did not pick up\.

In the [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) API, this metric is `SUM_RETRY_CALLBACK_ATTEMPTS`\.

Type: Integer

Category: contact record\-driven metric

## Callback contacts<a name="callback-contacts-historical"></a>

Count of contacts that were initiated from a queued callback\.
+ Type: Integer 
+ Category: contact record\-driven metric

## Callback contacts handled<a name="callback-contacts-handled-historical"></a>

Count of contacts that were initiated from a queued callback and handled by an agent\.

In the [GetMetricData](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricData.html) API, this metric is `CALLBACK_CONTACTS_HANDLED`\.

In the [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) API, this metric can be retrieved by using `CONTACTS_HANDLED` with a [MetricFilters](https://docs.aws.amazon.com/connect/latest/APIReference/API_MetricV2.html) parameter set as follows:
+ `MetricFilterKey` = `INITIATION_METHOD`
+ `MetricFilterValues` = `CALLBACK`

Type: Integer 

Category: contact record\-driven metric

## Contact disconnected<a name="contact-disconnected-historical"></a>

Sum of contacts disconnected in a queue\. The metric can be filtered by Disconnect Reason\.

In the [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) API, this metric is `SUM_CONTACTS_DISCONNECTED`\.
+ Type: Integer
+ Category: contact record\-driven metric

## Contact flow time<a name="contact-flow-time-historical"></a>

Total time a contact spent in a flow\.

Outbound contacts don't start in a flow, so outbound contacts aren't included\.
+ Type: String \(*hh:mm:ss*\)
+ Category: contact record\-driven metric

## Contact handle time<a name="contact-handle-time-historical"></a>

Total time that an agent spent on contacts, including [Customer Hold Time](#customer-hold-time-historical) and [After contact work time](#acw-historical)\. This includes any time spent on contacts while in a custom status\. \(Custom status = the agent's CCP status is other than **Available** or **Offline**\. For example, Training would be a custom status\.\)

Contact handle time is different from [Average handle time](#average-handle-time-historical)\. Contact handle time includes time spent in a custom status; Average handle time does not include it\.

**Tip**  
If you want to exclude the amount of time spent in a custom status, see [Agent on contact time](#agent-on-contact-time-historical)\. 
+ Type: String \(*hh:mm:ss*\)
+ Category: contact record\-driven metric

## Contact abandoned<a name="contacts-abandoned-historical"></a>

Count of contacts disconnected by the customer while in the queue\. Contacts queued for callback are not counted as abandoned\. When you create customized historical reports, to include this metric, on the **Groupings** tab choose either **Queue** or **Phone Number**\. 

In the [GetMetricData](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricData.html) and [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) APIs, this metric is `CONTACTS_ABANDONED`\.
+ Type: Integer 
+ Category: contact record\-driven metric

## Contacts abandoned in *X* seconds<a name="contacts-abandoned-x-historical"></a>

Count of contacts disconnected by the customer while in the queue for 0 to *X* seconds\. The possible values for *X* are: 15, 20, 25, 30, 45, 60, 90, 120, 180, 240, 300, and 600\.

In the [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) API, this metric is `SUM_CONTACTS_ABANDONED_IN_X`\. The API enables you to create custom duration to get this metric\. Choose from additional durations, such as minutes, hours, or days\. The maximum duration for a custom value is 7 days\. That's because in Amazon Connect you can't have a contact that goes longer than 7 days\.
+ Type: Integer 
+ Category: contact record\-driven metric

## Contacts agent hung up first<a name="contacts-agent-hung-up-first-historical"></a>

Count of contacts disconnected where the agent disconnected before the customer\.

In the [GetMetricData](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricData.html) API, this metric is `CONTACTS_AGENT_HUNG_UP_FIRST`\.

In the [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) API, this metric can be retrieved by using `CONTACTS_HANDLED` with a [MetricFilters](https://docs.aws.amazon.com/connect/latest/APIReference/API_MetricV2.html) parameter set as follows:
+ `MetricFilterKey` = `DISCONNECT_REASON`
+ `MetricFilterValues` = `AGENT_DISCONNECT`

Type: Integer 

Category: contact record\-driven metric

## Contacts answered in *X* seconds<a name="contacts-answered-x-historical"></a>

Count of contacts that were answered by an agent between 0 and *X* seconds of being placed in the queue, based on the value of [EnqueueTimestamp](ctr-data-model.md#EnqueueTimestamp-CTR)\. The possible values for *X* are: 15, 20, 25, 30, 45, 60, 90, 120, 180, 240, 300, and 600\.

In the [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) API, this metric is `SUM_CONTACTS_ANSWERED_IN_X`\. The API enables you to create custom duration to get this metric\. Choose from additional durations, such as minutes, hours, or days\. The maximum duration for a custom value is 7 days\. That's because in Amazon Connect you can't have a contact that goes longer than 7 days\.
+ Type: Integer 
+ Category: contact record\-driven metric

## Contacts created<a name="contacts-created-historical"></a>

Count of contacts in a queue\. The metric can be filtered by initiation methods\.

In the [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) API, this metric is `CONTACTS_CREATED`\.
+ Type: Integer
+ Category: contact record\-driven metric

## Contacts consulted<a name="contacts-consulted-historical"></a>

Deprecated May 2019\. When used in a report, it returns a dash \(\-\)\. 

Count of contacts handled by an agent who consulted with another agent in Amazon Connect\. The agent interacts with the other agent, but the customer is not transferred to the other agent\.

In the [GetMetricData](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricData.html) API, this metric is `CONTACTS_CONSULTED`\.
+ Type: Integer 
+ Category: contact record\-driven metric

## Contacts handled<a name="contacts-handled-historical"></a>

Count of contacts that were connected to an agent\.

It doesn’t matter how the contact got to the agent\. It could be a customer calling your contact center, or an agent calling the customer\. It could be a contact transferred from one agent to another\. It could be a contact where the agent answered it, but then they weren’t sure what to do and they transferred the contact away again\. As long as the agent was connected to the contact, it increments **Contacts handled**\. 

In the [GetMetricData](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricData.html) and [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) APIs, this metric is `CONTACTS_HANDLED`\.

Type: Integer 

Category: contact record\-driven metric

## Contacts handled incoming<a name="contacts-handled-incoming-historical"></a>

Count of incoming contacts that were handled by an agent, including inbound contacts and transferred contacts\.

In the [GetMetricData](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricData.html) API, this metric is `CONTACTS_HANDLED_INCOMING`\.

In the [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) API, this metric can be retrieved by using `CONTACTS_HANDLED` with a [MetricFilters](https://docs.aws.amazon.com/connect/latest/APIReference/API_MetricV2.html) parameter set as follows:
+ `MetricFilterKey` = `INITIATION_METHOD`
+ `MetricFilterValues` = `INBOUND`, `TRANSFER`, `QUEUE_TRANSFER`

Type: Integer 

Category: contact record\-driven metric

## Contacts handled outbound<a name="contacts-handled-outbound-historical"></a>

Count of outbound contacts that were handled by an agent\. This includes contacts that were initiated by an agent using the CCP\.

In the [GetMetricData](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricData.html) API, this metric is `CONTACTS_HANDLED_OUTBOUND`\.

In the [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) API, this metric can be retrieved by using `CONTACTS_HANDLED` with a [MetricFilters](https://docs.aws.amazon.com/connect/latest/APIReference/API_MetricV2.html) parameter set as follows:
+ `MetricFilterKey` = `INITIATION_METHOD`
+ `MetricFilterValues` = `OUTBOUND`

Type: Integer 

Category: contact record\-driven metric

## Contacts hold agent disconnect<a name="contacts-hold-agent-disconnect-historical"></a>

Count of contacts that were disconnected by the agent while the customer was on hold\.
+ Type: Integer 
+ Category: contact record\-driven metric

## Contacts hold customer disconnect<a name="contacts-hold-customer-disconnect-historical"></a>

Count of contacts that were disconnected by the customer while the customer was on hold\.

In the [GetMetricData](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricData.html) and [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) APIs, this metric is `CONTACTS_HOLD_ABANDONS`\.
+ Type: Integer 
+ Category: contact record\-driven metric

## Contacts hold disconnect<a name="contacts-hold-disconnect-historical"></a>

Count of contacts disconnected while the customer was on hold\. This includes both contacts disconnected by the agent and contacts disconnected by the customer\.
+ Type: Integer 
+ Category: contact record\-driven metric

## Contacts incoming<a name="contacts-incoming-historical"></a>

Count of incoming contacts, including inbound contacts and transferred contacts\.
+ Type: Integer 
+ Category: contact record\-driven metric

## Contacts missed<a name="contacts-missed-historical"></a>

Count of contacts routed to an agent but not answered by the agent, including contacts abandoned by the customer\. A contact can be counted as missed multiple times, once for each time it is routed to an agent but not answered\.

When you add this to a historical metrics report, it appears under the column named **Agent non\-response**\.

In the [GetMetricData](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricData.html) API, this metric is `CONTACTS_MISSED`\.

In the [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) API, this metric is `AGENT_NON_RESPONSE`\.

Type: Integer 

Category: Agent activity\-driven metric

## Contacts put on hold<a name="contacts-put-on-hold-historical"></a>

Count of contacts put on hold by an agent one or more times\.
+ Type: Integer 
+ Category: contact record\-driven metric

## Contacts queued<a name="contacts-queued-historical"></a>

Count of contacts placed in the queue\.

In the [GetMetricData](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricData.html) and [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) APIs, this metric is `CONTACTS_QUEUED`\.
+ Type: Integer 
+ Category: contact record\-driven metric

## Contacts transferred in<a name="contacts-transferred-in-historical"></a>

Count of contacts transferred in from queue to queue, and transferred in by an agent using the CCP\.

In the [GetMetricData](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricData.html) API, this metric is `CONTACTS_TRANSFERRED_IN`\.

In the [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) API, this metric can be retrieved by using `CONTACTS_CREATED` with a [MetricFilters](https://docs.aws.amazon.com/connect/latest/APIReference/API_MetricV2.html) parameter set as follows:
+ `MetricFilterKey` = `INITIATION_METHOD`
+ `MetricFilterValues` = `TRANSFER`, `QUEUE_TRANSFER`

Type: Integer 

Category: contact record\-driven metric

## Contacts transferred in by agent<a name="contacts-transferred-in-by-agent-historical"></a>

Count of contacts transferred in by an agent using the CCP\.

In the [GetMetricData](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricData.html) API, this metric is `CONTACTS_TRANSFERRED_IN_BY_AGENT`\.

In the [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) API, this metric can be retrieved by using `CONTACTS_CREATED` with a [MetricFilters](https://docs.aws.amazon.com/connect/latest/APIReference/API_MetricV2.html) parameter set as follows:
+ `MetricFilterKey` = `INITIATION_METHOD`
+ `MetricFilterValues` = `TRANSFER`

Type: Integer 

Category: contact record\-driven metric

## Contacts transferred in from queue<a name="contacts-transferred-in-from-queue-historical"></a>

Count of contacts transferred to the queue from another in a **Transfer to queue** flow\.

In the [GetMetricData](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricData.html) API, this metric is `CONTACTS_TRANSFERRED_IN_FROM_Q`\.

In the [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) API, this metric can be retrieved by using `CONTACTS_CREATED` with a [MetricFilters](https://docs.aws.amazon.com/connect/latest/APIReference/API_MetricV2.html) parameter set as follows:
+ `MetricFilterKey` = `INITIATION_METHOD`
+ `MetricFilterValues` = `QUEUE_TRANSFER`

Type: Integer 

Category: contact record\-driven metric

## Contacts transferred out<a name="contacts-transferred-out-historical"></a>

Count of contacts transferred out from queue to queue, and transferred out by an agent using the CCP\.

In the [GetMetricData](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricData.html) and [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) APIs, this metric is `CONTACTS_TRANSFERRED_OUT`\.
+ Type: Integer 
+ Category: contact record\-driven metric

## Contacts transferred out by agent<a name="contacts-transferred-out-by-agent-historical"></a>

Count of contacts transferred out by an agent using the CCP\.

In the [GetMetricData](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricData.html) and [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) APIs, this metric is `CONTACTS_TRANSFERRED_OUT_BY_AGENT`\.
+ Type: Integer 
+ Category: contact record\-driven metric

## Contacts transferred out external<a name="contacts-transferred-out-external-historical"></a>

Count of contacts that an agent transferred from the queue to an external source, such as a phone number other than the phone number for your contact center\.
+ Type: Integer 
+ Category: contact record\-driven metric

## Contacts transferred out queue<a name="contacts-transferred-out-from-queue-historical"></a>

Count of contacts transferred from the queue to another queue in a **Transfer to queue** flow\.

In the [GetMetricData](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricData.html) and [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) APIs, this metric is `CONTACTS_TRANSFERRED_OUT_FROM_QUEUE`\.
+ Type: Integer 
+ Category: contact record\-driven metric

## Contacts transferred out internal<a name="contacts-transferred-out-internal-historical"></a>

Count of contacts for the queue that an agent transferred to an internal source, such as a queue or another agent\. An internal source is any source that can be added as a quick connect\.
+ Type: Integer 
+ Category: contact record\-driven metric

## Customer hold time<a name="customer-hold-time-historical"></a>

Total time that customers spent on hold after being connected to an agent\. This includes time spent on a hold when being transferred, but does not include time spent in a queue\.
+ Type: String \(*hh:mm:ss*\)
+ Category: contact record\-driven metric

## Error status time<a name="error-status-time-historical"></a>

For a specific agent, the total time contacts were in an error status\. This metric can't be grouped or filtered by queue\. 
+ Type: String \(*hh:mm:ss*\)
+ Category: Agent activity\-driven metric

## Maximum queued time<a name="maximum-queued-time-historical"></a>

The longest time that a contact spent waiting in the queue\. This includes all contacts added to the queue, even if they were not connected with an agent, such as abandoned contacts\.

In the [GetMetricData](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricData.html) API, this metric is `QUEUED_TIME`\.

In the [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) API, this metric is `MAX_QUEUED_TIME`\.
+ Type: String \(*hh:mm:ss*\)
+ Category: contact record\-driven metric

## Non\-Productive Time<a name="npt-historical"></a>

Total time that agents spent in a [custom status](agent-custom.md)\. That is, their CCP status is other than **Available** or **Offline**\. 

This metric doesn't mean that the agent was spending their time unproductively\. 

**Tip**  
Agents can handle contacts while their CCP status is set to a custom status\. For example, agents can be **On contact** or doing **ACW** while their CCP is set to a custom status\. This means it's possible for agents to be counted as **On contact** and **NPT** at the same time\.   
For example, if an agent changes their status to a custom status, and then makes an outbound call, it would be counted as non\-productive time\.

This metric can't be grouped or filtered by queue\.
+ Type: String \(*hh:mm:ss*\)
+ Category: Agent activity\-driven metric

## Occupancy<a name="occupancy-historical"></a>

Percentage of time that agents were active on contacts\. This percentage is calculated as follows:

\(Agent on contact \(wall clock time\) / \(Agent on contact \(wall clock time\) \+ Agent idle time\)\) 

Where: 
+ \(Agent on contact \+ Agent idle time\) = total amount of agent time
+ So \(Agent on contact\)/\(total amount of agent time\) = percentage of time agents were active on contacts\.

**Important**  
**Occupancy** doesn't account for concurrency\. That is, an agent is considered 100% occupied for a given interval if they are handling at least one contact for that entire duration\.   
In the [GetMetricData](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricData.html) API, this metric is `OCCUPANCY`\.  
In the [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) API, this metric is `AGENT_OCCUPANCY`\.
+ Type: String
+ Min value: 0\.00%
+ Max value: 100\.00%
+ Category: Agent activity\-driven metric

## Online time<a name="online-time-historical"></a>

Total time that an agent spent with their CCP set to a status other than **Offline**\. This includes any time spent in a custom status\. This metric can't be grouped or filtered by queue, phone number, or channels\. 
+ Type: String
+ Category: Agent activity\-driven metric

## Scheduled time<a name="scheduled-time-historical"></a>

This metric is available only in AWS Regions where [Forecasting, capacity planning, and scheduling](regions.md#optimization_region) is available\.

Total time an agent was scheduled \(either for productive or non\-productive time\) and *Adherence* for those shifts was set to `Yes`\.

In the [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) API, this metric is `AGENT_SCHEDULED_TIME`\.
+ Type: String \(\(hh:mm:ss\)
+ Category: Agent activity\-driven metric

## Service level *X*<a name="service-level-historical"></a>

Percentage of contacts removed from the queue between 0 and *X* after being added to it\. A contact is removed from a queue when the following occurs: an agent answers the contact, the customer abandons the contact, or the customer requests a call back\. 

For *X* you can choose from pre\-set times in seconds: 15, 20, 25, 30, 45, 60, 90, 120, 180, 240, 300, and 600\. This percentage is calculated as follows:

\(Contacts removed from queue in *X* seconds / Contacts queued\) \* 100

In the [GetMetricData](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricData.html) and [GetMetricDataV2](https://docs.aws.amazon.com/connect/latest/APIReference/API_GetMetricDataV2.html) APIs, this metric is `SERVICE_LEVEL`\.
+ Type: String
+ Min value: 0\.00%
+ Max value: 100\.00%
+ Category: contact record\-driven metric

### Custom service levels<a name="custom-service-level-historical"></a>

You can also create custom service level metrics\. Choose from additional durations, such as minutes, hours, or days\.

Custom service levels are localized to the report where they are created\. For example, you create a report that has a custom service level of 75\. You leave the page and then create another report\. The custom service level 75 won't exist in the second report\. You'll need to create it again\. 

The maximum duration for a custom service level is 7 days\. That's because in Amazon Connect you can't have a contact that goes longer than 7 days\.

You can add up to 10 custom service levels per report\.