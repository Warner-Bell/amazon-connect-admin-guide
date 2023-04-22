# Flow block: Get customer input<a name="get-customer-input"></a>

## Description<a name="get-customer-input-description"></a>
+ It plays a prompt to get a response from the customer\. For example, "For Sales, press one\. For Support, press two\." 
+ When customers enter DTMF input \(touch\-tone keypad or telephone input\), the prompt is interruptible\. 
+ When an Amazon Lex bot plays a voice prompt, customers can interrupt it with their voice\. To set this up, use the `barge-in-enabled` session attribute\.
+ It then branches based on the customer's input\.
+ This block works for chat only when Amazon Lex is used\. It gathers customer input only, not agent input\. 

## Supported channels<a name="get-customer-input-channels"></a>

The following table lists how this block routes a contact who is using the specified channel\. 


| Channel | Supported? | 
| --- | --- | 
| Voice | Yes | 
| Chat | Yes when Amazon Lex is used Otherwise, No \- Error branch | 
| Task | Yes | 

## Flow types<a name="get-customer-input-types"></a>

You can use this block in the following [contact flow types](create-contact-flow.md#contact-flow-types):
+ Inbound flow
+ Customer queue flow
+ Transfer to Agent flow
+ Transfer to Queue flow

## Properties<a name="get-customer-input-properties"></a>

The following image shows the **Properties** page of the **Check call progress** block\. It is configured to play an audio prompt\. It branches on DTMF input, and times out after 5 seconds if the customer doesn't enter anything\.

![\[The properties page of the Get customer input block, the DTMF tab.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/get-customer-input-properties.png)

**Note**  
The **Get Customer Input** block does not currently support using a voice prompt from an S3 bucket with Amazon Lex V2\.  
For information about choosing a prompt from the Amazon Connect library or an S3 bucket, see the [Play prompt](play.md) block\. 

You can configure this block to accept DTMF input or a chat response\. You can also configure it work with Amazon Lex; for example, a contact can be routed based on their utterance\. To learn how to set up a Lex bot, see [Tutorial 3: Create an IT help desk](tutorial1-create-helpdesk.md)\. 

## DTMF tab properties<a name="get-customer-input-dtmf"></a>
+ **Audio prompt**: Select from a list of default audio prompts, or upload your own audio prompt\. 
+ **Set timeout**: Specify how long to wait while the user decides how they want to respond to the prompt\. The maximum timeout you can set is 179 seconds\.

## Amazon Lex tab properties<a name="get-customer-input-lex-tab-properties"></a>

------
#### [ Amazon Lex ]

**Note**  
Your language attribute in Amazon Connect must match the language model used to build your Amazon Lex V2 bot\. Set the language attribute using the [Set voice](set-voice.md) block or the [Set contact attributes](set-contact-attributes.md) block\.
+ **Lex bot properties**: After you create your Lex bot, enter the name and alias of the bot here\. Only built bots appear in the drop\-down list\. 

   The following image shows the Amazon Lex tab configured to use a Lex bot named **Help Desk \(US West: Oregon\)**\.  
![\[The properties page of the Get customer input block, the Amazon Lex tab.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/get-customer-input-properties2.png)
**Important**  
In a production environment, always use a different alias than **TestBotAlias** for Amazon Lex and **$LATEST** for Amazon Lex classic\. **TestBotAlias** and **$LATEST** support a limited number of concurrent calls to an Amazon Lex bot\. For more information, see [Runtime quotas](https://docs.aws.amazon.com/lexv2/latest/dg/quotas.html#quotas-service) or [Runtime Service Quotas \(Amazon Lex Classic\)](https://docs.aws.amazon.com/lex/latest/dg/gl-limits.html#gl-limits-runtime)\.
+ **Session attributes**: Specify attributes that apply to the current contact's session only\. The following image shows the session attributes configured for a max speech duration of 8000 milliseconds \(8 seconds\)\.  
![\[The properties page of the Get customer input block, the session attributes section.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/get-customer-input-properties3.png)
+ **Use sentiment override**: Branch based on sentiment score, before the Amazon Lex intent\. 

  The sentiment score is based on the last utterance of the customer\. It is not based on the entire conversation\.

  For example, a customer calls and they have a negative sentiment because their preferred appointment time isn't available\. You can branch the flow based on their negative sentiment score, for example, if their negative sentiment is more than 80%\. Or, a customer calls and has a positive sentiment of more than 80%, you can branch to upsell them on services\.

  The following image shows the Intents section of the Amazon Lex tab\. It is configured to route the contact when their negative sentiment score is 80%\.  
![\[The properties page of the Get customer input block, the Intents section.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/get-customer-input-properties5.png)

  If you add both negative and positive sentiment scores, the negative score is always evaluated first\. 

  For information about how to use sentiment score, alternative intents, and sentiment label with contact attributes, see [Check contact attributes](check-contact-attributes.md)\.

------
#### [ Amazon Lex \(Classic\) ]
+ **Lex bot properties**: After you create your Lex bot, enter the name and alias of the bot here\. Only published bots appear in the drop\-down list\. 

   The following image shows the Amazon Lex tab configured to use a Lex bot named **Help Desk \(US West: Oregon\)**\.  
![\[The properties page of the Get customer input block, the Amazon Lex (Classic) tab.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/get-customer-input-properties2.png)
**Important**  
In a production environment, always use a different alias than **TestBotAlias** for Amazon Lex and **$LATEST** for Amazon Lex classic\. **TestBotAlias** and **$LATEST** support a limited number of concurrent calls to an Amazon Lex bot\. For more information, see [Runtime quotas](https://docs.aws.amazon.com/lexv2/latest/dg/quotas.html#quotas-service) or [Runtime Service Quotas \(Amazon Lex Classic\)](https://docs.aws.amazon.com/lex/latest/dg/gl-limits.html#gl-limits-runtime)\.
+ **Session attributes**: Specify attributes that apply to the current contact's session only\. 

  The following image shows the session attributes configured for a max speech duration of 8000 milliseconds \(8 seconds\)\.  
![\[The session attributes section of the Amazon Lex tab.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/get-customer-input-properties3.png)

------

## Configurable time\-outs for voice input<a name="get-customer-input-configurable-timeouts"></a>

To configure time\-out values for voice contacts, use the following session attributes in the **Get customer input** block that calls your Lex bot\. These attributes allow you to specify how long to wait for the customer to finish speaking before Amazon Lex collects speech input from callers, such as answering a yes/no question, or providing a date or credit card number\. 

------
#### [ Amazon Lex ]
+ **Max Speech Duration**

  `x-amz-lex:audio:max-length-ms:[intentName]:[slotToElicit]`

  How long the customer speaks before the input is truncated and returned to Amazon Connect\. You can increase the time when a lot of input is expected or you want to give customers more time to provide information\. 

  Default = 12000 milliseconds \(12 seconds\)\. The maximum allowed value is 15000 milliseconds\. 
**Important**  
If you set **Max Speech Duration** to more than 15000 milliseconds, the contact is routed down the **Error** branch\. 
+ **Start Silence Threshold**

   `x-amz-lex:audio:start-timeout-ms:[intentName]:[slotToElicit]`

  How long to wait before assuming that the customer isn't going to speak\. You can increase the allotted time in situations where you'd like to allow the customer more time to find or recall information before speaking\. For example, you might want to give customers more time to get out their credit card so they can enter the number\. 

  Default = 3000 milliseconds \(3 seconds\)\.
+ **End Silence Threshold**

  `x-amz-lex:audio:end-timeout-ms:[intentName]:[slotToElicit] ` 

  How long to wait after the customer stops speaking before assuming the utterance has concluded\. You can increase the allotted time in situations where periods of silence are expected while providing input\. 

  Default = 600 milliseconds \(0\.6 seconds\)

------
#### [ Amazon Lex \(Classic\) ]
+ **Max Speech Duration**

  `x-amz-lex:max-speech-duration-ms:[intentName]:[slotToElicit]`

  How long the customer speaks before the input is truncated and returned to Amazon Connect\. You can increase the time when a lot of input is expected or you want to give customers more time to provide information\. 

  Default = 12000 milliseconds \(12 seconds\)\. The maximum allowed value is 15000 milliseconds\. 
**Important**  
If you set **Max Speech Duration** to more than 15000 milliseconds, the contact is routed down the **Error** branch\. 
+ **Start Silence Threshold**

   `x-amz-lex:start-silence-threshold-ms:[intentName]:[slotToElicit]`

  How long to wait before assuming that the customer isn't going to speak\. You can increase the allotted time in situations where you'd like to allow the customer more time to find or recall information before speaking\. For example, you might want to give customers more time to get out their credit card so they can enter the number\. 

  Default = 3000 milliseconds \(3 seconds\)\.
+ **End Silence Threshold**

  `x-amz-lex:end-silence-threshold-ms:[intentName]:[slotToElicit]` 

  How long to wait after the customer stops speaking before assuming the utterance has concluded\. You can increase the allotted time in situations where periods of silence are expected while providing input\. 

  Default = 600 milliseconds \(0\.6 seconds\)

------

## Configurable time\-outs for chat input during a Lex interaction<a name="get-customer-input-configurable-timeouts-chat"></a>

Use the **Chat timeout** field under **Intents** to configure timeouts for chat input\. Enter how long until inactive customers timeout in a Lex interaction\.
+ Minimum: 1 minute
+ Maximum: 7 days

The following image shows the **Get customer input** block configured to timeout chats when the customer is inactive for 2 minutes\.

![\[The Intents section of the properties page, the Chat timeout option.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/get-customer-input-chattimeout.png)

For information about setting up chat timeouts when all participants are human, see [Set up chat timeouts for chat participants](setup-chat-timeouts.md)\. 

## Barge\-in configuration and usage for Amazon Lex<a name="get-customer-input-bargein"></a>

You can allow customers to interrupt the Amazon Lex bot mid\-sentence using their voice, without waiting for it to finishing speaking\. Customers familiar with choosing from a menu of options, for example, can now do so without having to listen to the entire prompt\.

------
#### [ Amazon Lex ]
+ **Barge\-in**

  Barge\-in is enabled globally by default\. You can disable it in the Amazon Lex console\. For more information, see [Enabling your bot to be interrupted by your user](https://docs.aws.amazon.com/lexv2/latest/dg/interrupt-bot.html)\. Additionally, you can modify barge\-in behavior, by using the `allow-interrupt` session attribute\. For example, `x-amz-lex:allow-interrupt:*:*` allows interrupt for all intents and all slots\. For more information, see [ Configuring timeouts for capturing user input](https://docs.aws.amazon.com/lexv2/latest/dg/session-attribs-speech.html) in the *Amazon Lex V2 Developer Guide*\.

------
#### [ Amazon Lex \(Classic\) ]
+ **Barge\-in**

  `x-amz-lex:barge-in-enabled:[intentName]:[slotToElicit]`

  Barge\-in is disabled globally by default\. You must set the session attribute in the **Get customer input** block that calls your Lex bot to enable it at the global, bot, or slot levels\. This attribute only controls Amazon Lex barge\-in; it doesn't control DTMF barge\-in\. For more information, see [How to use Lex session attributes](how-to-use-session-attributes.md)\.

  The following image shows the **Session attributes** section with barge\-in enabled\.  
![\[The session attributes section of the properties page, Value set to true.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/barge-in-session-attribute.png)

------

## Configurable fields for DTMF input<a name="get-customer-input-configurable-dtmf"></a>

Use the following session attributes to specify how your Lex bot responds to DTMF input\. 
+ **End character**

  `x-amz-lex:dtmf:end-character:[IntentName]:[SlotName]`

  The DTMF end character that ends the utterance\. 

  Default = \# 
+ **Deletion character**

   `x-amz-lex:dtmf:deletion-character:[IntentName]:[SlotName]`

  The DTMF character that clears the accumulated DTMF digits and ends the utterance\. 

  Default = \*
+ **End timeout**

  `x-amz-lex:dtmf:end-timeout-ms:[IntentName]:[SlotName]` 

  The idle time \(in milliseconds\) between DTMF digits to consider the utterance as concluded\.

  Default = 5000 milliseconds \(5 seconds\)
+ **Max number of allow DTMF digits per utterance**

  `x-amz-lex:dtmf:max-length:[IntentName]:[SlotName]` 

  The maximum number of DTMF digits allowed in a given utterance\. This cannot be increased\.

  Default = 1024 characters

For more information, see [How to use Lex session attributes](how-to-use-session-attributes.md)\.

## Intents<a name="get-customer-input-intents"></a>
+ Enter the intents you created in Amazon Lex\. They are case sensitive\!

  The following image shows two intents in the Intents section: PasswordReset and NetworkIssue\.  
![\[The intents section of the properties page.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/tutorial1-configure-get-customer-input3.png)

## Configuration tips<a name="get-customer-input-tips"></a>
+ This topic explains some of the session attributes available for the integration with Amazon Lex\. For a list of all the available Amazon Lex session attributes, see [Configuring timeouts for capturing user input](https://docs.aws.amazon.com/lexv2/latest/dg/session-attribs-speech)\. 
+ When you use text, either for text\-to\-speech or chat, you can use a maximum of 3,000 billed characters \(6,000 total characters\)\.
+ Amazon Lex bots support both spoken utterances and keypad input when used in a flow\.
+ For both voice and DTMF, there can be only one set of session attributes per conversation\. Following is the order of precedence: 

  1. Lambda provided session attributes: Overrides to session attributes during customer Lambda invocation\.

  1. Amazon Connect console provided session attributes: Defined in the **Get customer input** block\.

  1. Service defaults: These are used only if no attributes are defined\.
+ You can prompt contacts to end their input with a pound key \# and to cancel it using the star key \*\. When you use a Lex bot, if you don't prompt customers to end their input with \#, they will end up waiting five seconds for Lex to stop waiting for additional key presses\. 
+ To control time\-out  functionality, you can use Lex session attributes in this block, or in set them in your Lex Lambda function\. If you choose to set the attributes in a Lex Lambda function, the default values are used until the Lex bot is invoked\. For more information, see [Using Lambda Functions](https://docs.aws.amazon.com/lex/latest/dg/using-lambda.html) in the *Amazon Lex Developer Guide*\. 
+ When you specify one of the session attributes described in this article, you can use wildcards\. They let you set multiple slots for an intent or bots\.

  Following are some examples of how you can use wildcards:
  + To set all slots for a specific intent, such as PasswordReset, to 2000 milliseconds:

    Name = `x-amz-lex:max-speech-duration-ms:PasswordReset:*`

    Value = 2000
  + To set all slots for all bots to 4000 milliseconds: 

    Name = `x-amz-lex:max-speech-duration-ms:*:*`

    Value = 4000

  Wildcards apply across bots but not across blocks in a flow\. 

  For example, you have a Get\_Account\_Number bot\. In the flow, you have two **Get customer input** blocks\. The first block sets the session attribute with a wildcard\. The second one doesn't set the attribute\. In this scenario, the change in behavior for the bot applies only to the first **Get customer input** block, where the session attribute is set\. 
+ Because you can specify that session attributes apply to the intent and slot level, you can specify that the attribute is set only when you're collecting a certain type of input\. For example, you can specify a longer **Start Silence Threshold** when you're collecting an account number than when you're collecting a date\. 
+ If DTMF input is provided to a Lex bot using Amazon Connect, the customer input is made available as a [Lex request attribute](https://docs.aws.amazon.com/lex/latest/dg/context-mgmt-request-attribs.html)\. The attribute name is `x-amz-lex:dtmf-transcript` and the value can be a maximum of 1024 characters\. 

  Following are different DTMF input scenarios:    
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/connect/latest/adminguide/get-customer-input.html)

  Where: 
  + \[DEL\] = Deletion character \(Default is **\*** \)
  + \[END\] = End character \(Default is **\#** \)

## Problems with DTMF input?<a name="use-multiple-input-blocks"></a>

Let's say you have the following scenario with two contacts flows, each one capturing DTMF input from customers: 

1. One flow uses the **Get customer input** block to request DTMF input from customers\.

1. After the DTMF input is entered, it uses the **Transfer to flow** block to move the contact to the next contact flow\.

1. In the next flow, there's a **Store customer input** block to get more DTMF input from the customer\.

There's setup time between the first and second flows\. This means if the customer enters DTMF input very quickly for the second flow, some of the DTMF digits might be dropped\.

For example, the customer needs to press 5, then wait for a prompt from the second flow, then type 123\. In this case, 123 is captured without problem\. However, if they don't wait for the prompt and enter 5123 very quickly, the **Store customer input** block may capture only 23 or 3\.

To guarantee the **Store customer input** block in second contact flow captures all of the digits, the customer needs to wait for the prompt to be played, and then enter their type DTMF input\.

## Configured block<a name="get-customer-input-configured"></a>

The following image shows an example of what this block looks like when it is configured\. It shows two branches for DTMF input: **Pressed 1** and **Pressed 2**\. It also shows branches for **Timeout**, **Default**, and **Error**\.

![\[A configured Get customer input block.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/get-customer-input-configured.png)

1. **Timeout**: What to do when the time in the **Set timeout** property has elapsed\.

1. **Default**: What to do if a customer enters a value other than 1 or 2\.

## Sample flows<a name="get-customer-input-samples"></a>

Amazon Connect includes a set of sample flows\. For instructions that explain how to access the sample flows in the flow designer, see [Sample flows](contact-flow-samples.md)\. Following are topics that describe the sample flows which include this block\.
+ [Sample inbound flow \(first contact experience\)](sample-inbound-flow.md)
+ [Sample interruptible queue flow with callback](sample-interruptible-queue.md) 
+ [Sample queue configurations](sample-queue-configurations.md) 
+ [Sample recording behavior](sample-recording-behavior.md) 

## Scenarios<a name="get-customer-input-scenarios"></a>

See these topics for scenarios that use this block:
+ [Add an Amazon Lex bot to Amazon Connect](amazon-lex.md)
+ [How to use the same bot for voice and chat](one-bot-voice-chat.md)
+ [Add text\-to\-speech to prompts](text-to-speech.md)