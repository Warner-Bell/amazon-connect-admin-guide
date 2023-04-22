# Flow block: Transfer to queue<a name="transfer-to-queue"></a>

## Description<a name="transfer-to-queue-description"></a>
+ In most types of flows, this block ends the current flow and places the customer in a queue\. 
+ When used in a Customer Queue flow, however, this block transfers a contact already in a queue to another queue\. 
+ When used in a callback scenario, Amazon Connect calls the agent first\. After the agent accepts the call in the CCP, Amazon Connect calls the customer\.

## Supported channels<a name="transfer-to-queue-channels"></a>

The following table lists how this block routes a contact who is using the specified channel\. 


| Channel | Supported? | 
| --- | --- | 
| Voice | Yes | 
| Chat | Yes | 
| Task | Yes | 

## Flow types<a name="transfer-to-queue-types"></a>

You can use this block in the following [contact flow types](create-contact-flow.md#contact-flow-types):
+ Inbound flow
+ Customer Queue flow
+ Transfer to Agent flow
+ Transfer to Queue flow

## Properties<a name="transfer-to-queue-properties"></a>

This block has two tabs on its properties page\. 

**Tab 1: Transfer to queue**: This tab is shown in the following image\.

![\[The properties page of the Transfer to queue block, the Transfer to queue tab.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/transfer-to-queue-properties.png)

When the **Transfer to queue** block runs, it checks the queue capacity to determine whether the queue is at capacity \(full\)\. This check for queue capacity compares the current number of contacts in the queue to the [Maximum contacts in queue](set-maximum-queue-limit.md) limit, if one is set for the queue\. 

If no limit is set, the queue is limited to the number of concurrent contacts set in the service quota for the instance\.

**Tab 2: Transfer to callback queue**: This tab is shown in the following image\.

![\[The properties page of the Transfer to queue block, the Transfer to callback queue tab.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/transfer-to-queue-properties1.png)

The following properties are available under the **Transfer to callback queue** tab:
+ **Initial delay**: Specify how much time has to pass between a callback contact being initiated in the flow, and the customer is put in queue for the next available agent\. 
+ **Maximum number of retries**: If this were set to 1, then Amazon Connect would try to callback the customer at most two times: the initial callback, and 1 retry\.
**Tip**  
We strongly recommend that you double\-check the number entered in **Maximum number of retries**\. If you accidentally enter a high number, such as 20, it's going to result in unnecessary work for the agent and too many calls for the customer\.
+ **Minimum time between attempts**: If the customer doesn't answer the phone, this is how long to wait until trying again\.
+ **Set working queue**: You can transfer a callback queue to a different queue\. This is useful if you set up a special queue just for callbacks\. You can then view that queue to see how many customers are waiting for callbacks\.
**Tip**  
If you want to specify the **Set working queue** property, you need to add a **Set customer callback number** block before this block\.

  If you don't set a working queue, Amazon Connect uses the queue that was set previously in the flow\.

## Configuration tips<a name="transfer-to-queue-tips"></a>
+ When you use this block in a Customer Queue flow, you must add a **Loop prompts** block before this one\.
+ To use this block in most flows, you must add a **Set working queue** block first\. The one exception to this rule is when this block is used in a Customer Queue flow\. 
+ When you use text, either for text\-to\-speech or chat, you can use a maximum of 3,000 billed characters \(6,000 total characters\)\.
+ Amazon Lex bots support both spoken utterances and keypad input when used in a flow\.
+ You can prompt contacts to end their input with a pound key \# and to cancel it using the star key \*\. 

## Configured block<a name="transfer-to-queue-configured"></a>

 When this block is configured to **transfer to queue**, it looks similar to the following image\. It has two branches: **At capacity** and **Error**\. If a contact is routed down the **At capacity** branch, it remains in the current working queue\.

![\[A configured transfer to queue block.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/transfer-to-queue-configured.png)

When this block is configured to **transfer to callback queue**, it looks similar to the following image\. It has two branches: **Success** and **Error**\. If a contact is routed down the **Success** branch, it's transferred to the specified queue\.

![\[A configured transfer to callback block.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/transfer-to-queue-configured1.png)

## Scenarios<a name="transfer-to-queue-scenarios"></a>

See these topics for scenarios that use this block:
+ [Manage contacts in a queue](queue-to-queue-transfer.md)
+ [](setup-queued-cb.md)
+ [About queued callbacks in metrics](about-queued-callbacks.md)

## Sample flows<a name="transfer-to-queue-samples"></a>

Amazon Connect includes a set of sample flows\. For instructions that explain how to access the sample flows in the flow designer, see [Sample flows](contact-flow-samples.md)\. Following are topics that describe the sample flows which include this block\.
+ [Sample queue configurations](sample-queue-configurations.md)
+ [Sample customer queue priority](sample-customer-queue-priority.md)
+ [Sample queued callback](sample-queued-callback.md)