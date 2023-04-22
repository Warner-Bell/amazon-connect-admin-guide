# Flow block: Loop prompts<a name="loop-prompts"></a>

## Description<a name="loop-prompts-description"></a>
+ Loops a sequence of prompts while a customer or agent is on hold or in queue\.

## Supported channels<a name="loop-prompts-channels"></a>

The following table lists how this block routes a contact who is using the specified channel\. 


| Channel | Supported? | 
| --- | --- | 
| Voice | Yes | 
| Chat | No \- Error branch | 
| Task | No \- Error branch | 

## Flow types<a name="loop-prompts-types"></a>

You can use this block in the following [contact flow types](create-contact-flow.md#contact-flow-types):
+ Customer Queue flow
+ Customer Hold flow
+ Agent Hold flow

## Properties<a name="loop-prompts-properties"></a>

The following image shows the **Properties** page of the **Loop prompts** block\. It shows there are three types of prompts you can choose from the dropdown list: **Audio recording**, **Text to Speech**, **S3 file path**\.

![\[The properties page of the Loop prompts block, the dropdown list of prompt types.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/loop-prompts-properties.png)

### How the Interrupt option works<a name="loop-prompts-properties-interrupt"></a>

Let's say you have multiple prompts and you set **Interrupt** to 60 seconds\. Following is what will happen: 
+ The block plays prompts in the order that they are listed for the entirety of the prompt length\.
+ If the combined play time for the prompts is 75 seconds, after 60 seconds the prompt is interrupted and reset to the 0 second point again\. 
+ It's possible your customers would never hear potentially important information that is supposed to play after 60 seconds\. 

This scenario is especially possible when using the default audio prompts that Amazon Connect provides since these audio prompts can be as long as 4 minutes\. 

## Configuration tips<a name="loop-prompts-tips"></a>
+ The following blocks are not allowed before the **Loop prompts** block: 
  + [Get customer input](get-customer-input.md)
  + [Loop](loop.md)
  + [Play prompt](play.md)
  + [Start media streaming](start-media-streaming.md)
  + [Stop media streaming](stop-media-streaming.md)
  + [Store customer input](store-customer-input.md)
  + [Transfer to phone number](transfer-to-phone-number.md)
  + [Transfer to queue](transfer-to-queue.md), including **Transfer to callback queue**
+ For information about choosing a prompt from the Amazon Connect library or an S3 bucket, see the [Play prompt](play.md) block\. 
+ When **Loop prompts** is used in a Queue flow, audio playback can be interrupted with a flow at preset times\.
+ Always use an interruption period that's greater than 20 seconds\. This is the amount of time an available agent has to accept the contact\. If the interruption period is less than 20 seconds, you might get contacts going down the **Error** branch\. This is because Amazon Connect doesn't support dequeuing the customer when they are being routed to an active agent and are in the 20 second window to join\.
+ The internal counter for the loop is persisted for the call, not the flow\. If you reuse the flow during a call, the loop counter isn't reset\.
+ If this block is triggered during a chat conversation, the contact is routed down the **Error** branch\.
+ Some existing flows have a version of the **Loop prompts** block that doesn't have an **Error** branch\. In this case, a chat contact stops execution of the customer queue flow\. The chat is routed when the next agent becomes available\.

## Configured block<a name="loop-prompts-configured"></a>

The following image shows what this block looks like when it is configured to play a prompt from the Amazon Connect library\. Choose \+ next to **Audio Recording** to view the full name of the file\. The configured block has two branches: **Timeout** and **Error**\.

![\[A Loop prompts block configured to play a prompt from the Amazon Connect library.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/loop-prompts-configured.png)

The following image shows what this block looks like when it is configured to play a prompt from Amazon S3\. Choose \+ next to **S3 path** to view the full path\. The configured block has two branches: **Timeout** and **Error**\.

![\[A Loop prompts block configured to play a prompt from Amazon S3.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/loop-prompts-configured2.png)

## Sample flows<a name="loop-prompts-samples"></a>

Amazon Connect includes a set of sample flows\. For instructions that explain how to access the sample flows in the flow designer, see [Sample flows](contact-flow-samples.md)\. Following are topics that describe the sample flows which include this block\.
+ [Sample interruptible queue flow with callback](sample-interruptible-queue.md)

## Scenarios<a name="loop-prompts-scenarios"></a>

See these topics for scenarios that use this block:
+ [Manage contacts in a queue](queue-to-queue-transfer.md)