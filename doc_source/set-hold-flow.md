# Flow block: Set hold flow<a name="set-hold-flow"></a>

## Description<a name="set-hold-flow-description"></a>
+ Links from one flow type to another\.
+ Specifies the flow to invoke when a customer or agent is put on hold\.

  If this block is triggered during a chat conversation, the contact is routed down the **Error** branch\.

## Supported channels<a name="set-hold-channels"></a>

The following table lists how this block routes a contact who is using the specified channel\. 


| Channel | Supported? | 
| --- | --- | 
| Voice | Yes | 
| Chat | No \- Error branch | 
| Task | No \- Error branch | 

## Flow types<a name="set-hold-flow-types"></a>

You can use this block in the following [contact flow types](create-contact-flow.md#contact-flow-types):
+ Inbound flow
+ Customer Queue flow
+ Outbound whisper flow
+ Transfer to Agent flow
+ Transfer to Queue flow

## Properties<a name="set-hold-flow-properties"></a>

The following image shows the **Properties** page of the **Set hold flow** block\. It shows the dropdown list of namespaces that you can use to set the hold flow dynamically\.

![\[The properties page of the Set hold flow block.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/set-hold-flow-properties.png)

For information about using attributes, see [Use Amazon Connect contact attributes](connect-contact-attributes.md)\.

## Configured block<a name="set-hold-flow-configured"></a>

The following image shows an example of what this block looks like when it is configured\. It has the following branches: **Success** and **Error**\.

![\[A configured set hold flow block.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/set-hold-flow-configured.png)