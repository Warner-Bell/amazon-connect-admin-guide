# Flow block: Wisdom<a name="wisdom"></a>

## Description<a name="wisdom-description"></a>
+ Associates a Wisdom domain to a contact to enable real\-time recommendations\.
+ For more information about enabling Wisdom, see [Deliver information to agents using Amazon Connect Wisdom](amazon-connect-wisdom.md)\. 

## Supported channels<a name="wisdom-channels"></a>

The following table lists how this block routes a contact who is using the specified channel\. 

**Note**  
Nothing happens if a chat or task is sent to this block, however, **you will be charged**\. To prevent this, add a [Check contact attributes](check-contact-attributes.md) block before this one and route chats and tasks accordingly\. For instructions, see [Route based on contact's channel](use-channel-contact-attribute.md)\.


| Channel | Supported? | 
| --- | --- | 
| Voice | Yes | 
| Chat | No | 
| Task | No | 

## Flow types<a name="wisdom-types"></a>

You can use this block in the following [contact flow types](create-contact-flow.md#contact-flow-types):
+ Inbound flow
+ Customer Queue flow
+ Outbound whisper flow
+ Transfer to Agent flow
+ Transfer to Queue flow

## Properties<a name="wisdom-properties"></a>

The following image shows the **Properties** page of the **Wisdom** block\. It specifies the full Amazon Resource Name \(ARN\) of the Wisdom domain to associate to the contact\.

![\[The properties page of the Wisdom block.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/wisdom-block-properties.png)

## Configuration tips<a name="wisdom-tips"></a>
+ Amazon Connect Wisdom, along with Contact Lens Real\-Time analytics, is used to recommend content that is related to customer issues detected during the current contact\. The [Set recording and analytics behavior](set-recording-behavior.md) block with Contact Lens real\-time enabled must also be set in this flow for Wisdom recommendations to work\. It doesn’t matter where in the flow you add [Set recording and analytics behavior](set-recording-behavior.md)\. 

## Configured block<a name="wisdom-configured"></a>

The following image shows an example of what this block looks like when it is configured\. It has the following branches: **Success** and **Error**\. 

![\[A configured Wisdom block.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/wisdom-block-configured.png)