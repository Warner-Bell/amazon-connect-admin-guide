# Flow block: Start media streaming<a name="start-media-streaming"></a>

## Description<a name="start-media-streaming-description"></a>

Captures what the customer hears and says during a contact\. You can then perform analysis on the audio streams to:
+ Determine customer sentiment\.
+ Use the audio for training purposes\.
+ Identify and flag abusive callers\.

## Supported channels<a name="start-media-channels"></a>

The following table lists how this block routes a contact who is using the specified channel\. 


| Channel | Supported? | 
| --- | --- | 
| Voice | Yes | 
| Chat | No \- Error branch | 
| Task | No \- Error branch | 

## Flow types<a name="start-media-streaming-types"></a>

You can use this block in the following [contact flow types](create-contact-flow.md#contact-flow-types):
+ Inbound flow
+ Customer Queue flow
+ Customer Whisper flow
+ Outbound Whisper flow
+ Transfer to Agent flow
+ Transfer to Queue flow

## Properties<a name="start-media-streaming-properties"></a>

The following image shows the **Properties** page of the **Start media streaming** block\. It has two options: start the stream from the customer or to the customer\. 

![\[The properties page of the Start media streaming block.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/start-media-streaming.png)

## Configuration tips<a name="start-media-streaming-tips"></a>
+ You must enable live media streaming in your instance to successfully capture customer audio\. For instructions, see [Capture customer audio: live media streaming](customer-voice-streams.md)\.
+ Customer audio is captured until a **Stop media streaming** block is invoked, even if the contact is passed to another flow\.
+ You must use a **Stop media streaming** block to stop media streaming\.
+ If this block is triggered during a chat conversation, the contact is routed down the **Error** branch\.

## Configured block<a name="start-media-streaming-configured"></a>

The following image shows an example of what this block looks like when it is configured\. It has the following branches: **Success** and **Error**\.

![\[A configured Start media streaming block.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/start-media-streaming-configured.png)

## Sample flows<a name="start-media-streaming-samples"></a>

Amazon Connect includes a set of sample flows\. For instructions that explain how to access the sample flows in the flow designer, see [Sample flows](contact-flow-samples.md)\. Following are topics that describe the sample flows which include this block\.

[Example flow for testing live media streaming](use-media-streams-blocks.md) 