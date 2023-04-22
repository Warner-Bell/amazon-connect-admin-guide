# Flow block: Get queue metrics<a name="get-queue-metrics"></a>

## Description<a name="get-queue-metrics-description"></a>
+ Retrieves near real\-time metrics, with a delay of 5\-10 seconds, from a queue so you can make routing decisions\. If there is no current activity in your contact center, nothing is returned for these metrics\. 

  Following are the metrics that can be retrieved:
  + [Queue name](real-time-metrics-definitions.md#queue-real-time) 
  + Queue ARN\. 
  + [Contacts in queue](real-time-metrics-definitions.md#in-queue-real-time)
  + [Oldest contact in queue](real-time-metrics-definitions.md#oldest-real-time)
  + [Agents online](real-time-metrics-definitions.md#online-real-time)
  + [Agents available](real-time-metrics-definitions.md#available-real-time)
  + [Agents staffed](real-time-metrics-definitions.md#staffed-real-time)
  + [Agents after contact work](real-time-metrics-definitions.md#aftercallwork-real-time)
  + [Agents busy](real-time-metrics-definitions.md#on-call-real-time): Although this option maps to the **On contact** real\-time metric, note that **On contact** includes ACW but **Agents busy** does not\.
  + [Agents missed](real-time-metrics-definitions.md#agent-non-response-real-time) \(Agent non\-response\)
  + [Agents non\-productive](real-time-metrics-definitions.md#non-productive-time-real-time)
+ You can choose to return metrics by channel, for example, voice or chat\. You can also filter by queue or agent\. These options enable you to know how many chat and voice contacts are in a queue and if you have agents available to handle those contacts\. 
+ You can route contacts based on queue status, such as number of contacts in queue or agents available\. Queue metrics are aggregated across all channels and are returned as attributes\. The current queue is used by default\.
+ After a **Get queue metrics** block, use a [Check contact attributes](check-contact-attributes.md) to check metric values and define routing logic based on them, such as number of contacts in a queue, number of available agents, and oldest contact in a queue\. 

## Supported channels<a name="get-queue-metrics-channels"></a>

The following table lists how this block routes a contact who is using the specified channel\. 


| Channel | Supported? | 
| --- | --- | 
| Voice | Yes | 
| Chat | Yes | 
| Task | Yes | 

## Flow types<a name="get-queue-metrics-types"></a>

You can use this block in the following [contact flow types](create-contact-flow.md#contact-flow-types):
+ All flows

## Properties<a name="get-queue-metrics-properties"></a>

The following image shows the **Properties** page of the **Get queue metrics** block\. It is configured to retrieve metrics for the **Voice** channel\.

![\[The properties page of the Get queue metrics block.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/get-queue-metrics-properties1.png)

You can retrieve metrics by channel, and/or by queue or agent\.
+ If you don't specify a channel, it returns metrics for all channels\. 
+ If you don't specify a queue, it returns metrics for the current queue\.
+ Dynamic attributes can only return metrics for one channel\. 

For example, the following image shows the **Properties** page configured for the **Chat** channel and **BasicQueue**\. If you choose these settings **Get queue metrics** would return metrics for only the BasicQueue, filtered to include only chat contacts\. 

![\[The optional parameters section of the Properties page.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/get-queue-metrics-properties3.png)

## Configuration tips<a name="get-queue-metrics-tips"></a>

### Specifying a channel in the Set contact attributes block<a name="get-queue-metrics-tips1"></a>

Dynamic attributes can only return metrics for one channel\.

Before you use dynamic attributes in the **Get queue metrics** block, you need to set the attributes in the [Set contact attributes](set-contact-attributes.md) block, and specify which channel\.

When you set a channel dynamically using text, as shown in the following image, for the attribute value enter **Voice** or **Chat**\. This value is not case\-sensitive\. 

![\[The properties page of the Set contact attributes block, Value set to chat.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/get-queue-metrics-properties2.png)

### Using the Check contact attributes block after the Get queue metrics block<a name="get-queue-metrics-tips2"></a>

After a **Get queue metrics** block, add a [Check contact attributes](check-contact-attributes.md) block to branch based on the returned metrics\. Use the following steps:

1. After **Get queue metrics**, add a **Check contact attributes** block\.

1. In the **Check contact attributes** block, set **Attribute to check** to **Queue metrics**\.

1. In the **Value** dropdown box, you'll see a list of queue metrics that can be checked by the **Get queue metrics** block\. Choose the metric that you want to use for the routing decision\.   
![\[Attribute to check section, dropdown list of available metrics.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/get-queue-metrics-block-returned-metrics.png)

## Configured block<a name="get-queue-metrics-configured"></a>

The following image shows an example of what this block looks like when it is configured\. It has two branches: **Success** and **Error**\.

![\[A configured Get queue metrics block.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/get-queue-metrics-configured.png)

## Scenarios<a name="get-queue-metrics-scenarios"></a>

See these topics for scenarios that use this block:
+ [How to reference contact attributes](how-to-reference-attributes.md)