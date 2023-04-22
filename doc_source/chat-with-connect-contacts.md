# How to use the CCP to chat with contacts<a name="chat-with-connect-contacts"></a>

When you set your status in the CCP to **Available**, Amazon Connect delivers calls or chats to you, based on the settings in your [routing profile](routing-profiles.md)\. An administrator can specify that up to 10 chat conversations can be routed to you at the same time\. 

You can't initiate chat conversations from the CCP\.

**Note**  
IT Administrators: To enable customers and agents to send attachments, such as files, through the chat interface, see [Enable attachments to share files using chat](enable-attachments.md)\.

When a chat contact arrives, here's how you are notified:

1. If you enabled notifications in your browser, you'll get a pop\-up notification at the bottom of your screen, like this:   
![\[A browser notification of incoming chat.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/chat-notify.png)

1. If you're on the chat tab, the page displays the name of the contact and a button for you to connect to the chat\.  
![\[The ccp, the incoming chat notification, the accept chat button.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/incoming-chat-ccp.png)

1. If you're on the phone tab, a banner displays the name of the contact and a button for you to connect to the chat\.  
![\[The ccp, a banner displays incoming chat.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/chat-incoming-banner.png)

1. You have 20 seconds to accept or reject a contact\. If you're on a chat, and another comes in but you don't accept it, a tab appears indicating the chat was missed\.  
![\[The ccp, the missed chat tab.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/missed-chat-tab.png)

1. Choose **Accept chat** to connect to the contact\. 
**Note**  
Chat conversations must be accepted manually\. There's no auto\-accept for these conversations\.

1. You'll see the full transcript of what the contact has already typed\. If applicable, you'll also see what a bot or another agent has entered\. In the following image, **John** is the name of the customer, **BOT** is the Amazon Lex bot, and **Jane** is the name of the agent\.   
![\[The ccp, a connect chat, the transcript between customer and bot.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/ccp-chat-agent.png)

## What do the timers at the top of the chat tabs mean?<a name="timer-in-chat-windows"></a>

When you're in a chat conversation with a contact, you'll see two timers at the top of the chat tab\. These timers tell you: 
+ How long the contact has been connected to your contact center\. This includes the time spent with the bot, if you're using one\.
+ How long since the last text was sent\. This can be either from the customer to the agent, or from the agent to the customer\. The timer is reset with texts message between the two\. It is not reset with each consecutive text message sent from a participant\.

![\[The ccp, the timers at top of chat tabs.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/chat-timers.png)

If you have multiple chat tabs open, an hour glass appears letting you know which ones are in an After Contact Work \(ACW\) state\. The timer indicates how long the contact has been in ACW\. 

![\[The ccp, the hour glass icon.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/chat-acw.png)

## What happens to missed chats?<a name="missed-chats"></a>

Let's say you take a break but forget to change your status in the CCP from **Available** to **Break**\. Amazon Connect tries to route a chat to you for 20 seconds\. Keep in mind that your admin can't configure this amount of time\. 

After 20 seconds, the contact is counted as [Agent non\-response](real-time-metrics-definitions.md#agent-non-response-real-time) in the real\-time metrics report and the historical metrics report\.

When you return from break and choose the chat tab, you'll see the missed contacts and how long they've been there\. Each contact occupies a slot\. This way, with all of your slots are occupied, Amazon Connect won't route any more contacts to you\.

![\[The ccp, a missed chat, the name of the agent who is logged in.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/missed-chat-name.png)

You can clear the slots so that chats are routed to you again\. For each missed contact, choose the banner, and then choose **Clear contact**\. 

## How to format messages<a name="format-chats"></a>

When composing a chat message, you have the ability to format your message\. This enables you to add structure and clarity to your support messages\. You can add the following formatting: 
+ Bold
+ Italic
+ Bulleted list
+ Numbered list
+ Hyperlinks
+ Emoji
+ Attachments

To get started, highlight the text you want to format, and then select a the formatting options from the toolbar at the bottom of the chat window\. You can see exactly what the message looks like before sending it\.

![\[The ccp, the formatting toolbar at the bottom of the chat window.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/chat-rich-messaging-toolbar.png)

**Tip**  
Developers: Enable this feature from the chat user interface\. For instructions, see [Enable text formatting for your customer's chat experience](enable-text-formatting-chat.md)\.