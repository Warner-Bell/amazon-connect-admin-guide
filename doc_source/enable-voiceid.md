# Enable Voice ID<a name="enable-voiceid"></a>

## Before you begin<a name="enable-voiceid-requirements"></a>

Before you get started, complete the following tasks\.

**Topics**
+ [Grant the required permissions](#enable-voiceid-permissions)
+ [Decide how to name your Voice ID domain](#enable-voiceid-domains)
+ [Create an AWS KMS key to encrypt data stored in the domain](#enable-voiceid-awsmanagedkey)

### Grant the required permissions<a name="enable-voiceid-permissions"></a>

You must grant the required permissions to users, groups, or roles\. For more information, see [AmazonConnectVoiceIDFullAccess](security_iam_awsmanpol.md#amazonconnectvoiceidfullaccesspolicy)\.

Access to Voice ID APIs using the Contact Control Panel \(CCP\) is disabled by default\.

### Decide how to name your Voice ID domain<a name="enable-voiceid-domains"></a>

When you enable Voice ID, you are prompted to provide a friendly domain name that's meaningful to you such as your organization name, for example, *Voice ID\-ExampleCorp*\. 

### Create an AWS KMS key to encrypt data stored in the domain<a name="enable-voiceid-awsmanagedkey"></a>

When you enable Voice ID, you are prompted to create or provide an [AWS KMS key](https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html#kms_keys)\. It encrypts the customer data stored by Voice ID such as audio files, voiceprints, and the speaker identifiers\.

Step\-by\-step instructions for creating these KMS keys are provided in [Step 2: Create a new Voice ID domain and encryption key](#enable-voiceid-step2)\.

Data at rest—specifically, freeform fields that you provide plus audio files/voiceprints—are encrypted under the KMS key you choose\. Your customer managed key is created, owned, and managed by you\. You have full control over the KMS key \(AWS KMS charges apply\)\.

When making calls to Voice ID for anything other than `CreateDomain` or `UpdateDomain`, the user making the call requires `kms:Decrypt` permissions for the key associated with the domain\. When making calls to `CreateDomain` or `UpdateDomain`, the user also requires `kms:DescribeKey` and `kms:CreateGrant` permissions for the key\. When you create \(or update\) a Voice ID domain, it creates a grant on the KMS key so that it can be used by Voice ID asynchronous processes \(such as speaker enrollment\) and by the Amazon Connect service\-linked role during your flows\. This grant includes an encryption context specifying the domain with which the key is associated\. For more on grants, see [Using grants](https://docs.aws.amazon.com/kms/latest/developerguide/grants.html) in the AWS Key Management Service Developer Guide\.

If you create a domain and associate it with one key, store some data, and then change the KMS key to a different key, an asynchronous process will be triggered to re\-encrypt the old data with the new KMS key\. After this process completes, all of your domain's data will be encrypted under the new KMS key, and you may safely retire the old key\. For more information, see [UpdateDomain](https://docs.aws.amazon.com/voiceid/latest/APIReference/API_UpdateDomain)\.

**Tip**  
You can create KMS keys or provide an existing KMS key programmatically\. For more information, see [Amazon Connect Voice ID APIs](https://docs.aws.amazon.com/voiceid/latest/APIReference/)\.

## Step 1: Read the BIPA Consent Acknowledgement<a name="enable-voiceid-step1"></a>

Reading the Biometric Privacy Act \(BIPA\) Consent Acknowledgement is a requirement to enable Voice ID\. You need to do this once per account, across all Regions\. You cannot do this step by using APIs\. For more information about BIPA, see this Wikipedia article: [Biometric Information Privacy Act](https://en.wikipedia.org/wiki/Biometric_Information_Privacy_Act)\. 

1. Open the Amazon Connect console at [https://console\.aws\.amazon\.com/connect/](https://console.aws.amazon.com/connect/)\.

1. On the instances page, choose the instance alias\. The instance alias is also your **instance name**, which appears in your Amazon Connect URL\. The following image shows the **Amazon Connect virtual contact center instances** page, with a box a box around the instance alias\.  
![\[The Amazon Connect virtual contact center instances page, the instance alias.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/instance.png)

1. In the navigation pane, choose **Voice ID**\. Read the BIPA Consent Acknowledgement, and accept if you agree\.  
![\[The Enable Voice ID page, the button that says Read the BIPA Consent Acknowledgement.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/voiceid-bipa.png)

## Step 2: Create a new Voice ID domain and encryption key<a name="enable-voiceid-step2"></a>

You can perform this step using the Amazon Connect console or by using Amazon Connect and Voice ID APIs\. 

------
#### [ Amazon Connect console instructions ]

1. In the **Domain setup** section, choose **Create a new domain**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/voiceid-enable-domain.png)

1. In the **Domain name** box, enter a friendly name that's meaningful to you, such as your organization name, for example, *VoiceID\-ExampleCorp*\.

1. Under **Encryption**, create or enter your own AWS KMS key for encrypting your Voice ID domain\. Following are the steps to create your KMS key key:

   1. Choose **Create KMS key**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/voiceid-create-kms-key.png)

   1. A new tab in your browser opens for the Key Management Service \(KMS\) console\. On the **Configure key** page, choose **Symmetric**, and then choose **Next**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/customer-profiles-create-kms-key-configure-key.png)

   1. On the **Add labels** page, add a name and description for the KMS key, and then choose **Next**\.

   1. On the **Define key administrative permissions** page, choose **Next**\.

   1. On the **Define key usage permissions** page, choose **Next**\.

   1. On the **Review and edit key policy** page, choose **Finish**\.

   1. Return to the tab in your browser for the Amazon Connect console, **Voice ID** page\. Click or tap in the **AWS KMS key** for the key you created to appear in a dropdown list\. Choose the key you created\.

1. Choose **Enable Voice ID**\. 

------
#### [ API instructions ]

1. Call the [CreateDomain](https://docs.aws.amazon.com/voiceid/latest/APIReference/API_CreateDomain.html) API to create a new Voice ID domain\.

1. Call the [CreateIntegrationAssociation](https://docs.aws.amazon.com/connect/latest/APIReference/API_CreateIntegrationAssociation.html) API to associate the Voice ID domain with the Amazon Connect instance\.

   1. Pass the ARN of the Voice ID domain just created into the `IntegrationArn` parameter\. For `IntegrationType` use `VOICE_ID`\.

------

You've enabled Voice ID for your instance\. The following has been created: 
+ Your Voice ID domain and a default fraudster watchlist that will hold your fraudsters\.
+ A managed Amazon EventBridge rule in your account\. This rule is used to ingest Voice ID events for creating contact records related to Voice ID\. Additionally, Amazon Connect adds [Voice ID permissions](connect-slr.md) to the service\-linked role for Amazon Connect\.

Next, in Step 3 you configure how you want Voice ID to work in your flow\.

## Step 3: Configure Voice ID in your contact flow<a name="enable-voiceid-step3"></a>

In this step you add the required blocks to your flow and configure how you want Voice ID to work\.
+ [Play prompt](play.md): Add this block before the [Set Voice ID](set-voice-id.md) block to stream audio properly\. You can edit it to include a simple message such as "Welcome\."
+ [Set Voice ID](set-voice-id.md): After the [Play prompt](play.md) block, add the [Set Voice ID](set-voice-id.md) block\. It should be at the start of a call\. Use this block to start streaming audio to Amazon Connect Voice ID to verify the caller's identity, as soon as the call is connected to a flow\. 

  In **Set Voice ID** block you configure the authentication threshold, response time, fraud threshold, and fraudster watchlist to be used for known fraudster detection\.
+ [Set contact attributes](set-contact-attributes.md): Use to pass the `CustomerId` attribute to Voice ID\. The `CustomerId` may be a customer number from your CRM, for example\. You can create a Lambda function to pull the unique customer ID of the caller from your CRM system\. Voice ID uses this attribute as the `CustomerSpeakerId` for the caller\.
**Note**  
`CustomerId` can be an alphanumeric value\. It supports only \_ and \- \(underscore and hyphen\) special characters\. It does not need to be UUID\. For more information, see `CustomerSpeakerId` in the [Speaker](https://docs.aws.amazon.com/voiceid/latest/APIReference/API_Speaker.html) data type\.
+ [Check Voice ID](check-voice-id.md): Use to check the response from Voice ID for enrollment status, voice authentication, and fraud detection, and then branch based on one of the returned statuses\.

### Example Voice ID flow<a name="sample-voiceid-flow"></a>

**Caller not enrolled**

1. When a customer calls for the first time, their `CustomerId` is passed to Voice ID using the [Set contact attributes](set-contact-attributes.md) block\.

1. Voice ID looks for `CustomerId` in its database\. Since it's not there, it sends a **Not enrolled** result message\. The [Check Voice ID](check-voice-id.md) block branches based on this result, and you can decide what the next step should be\. For example, you might want agents to enroll the customer in voice authentication\.

1. Voice ID starts listening to the customer's speech after the contact has encountered the [Set Voice ID](set-voice-id.md) block, where Voice ID is enabled\. It listens until it accummulates 30 seconds of net speech or the call ends, whichever happens first\.

**Caller enrolled**

1. The next time the customer calls, Voice ID finds their `CustomerId` in the database\. 

1. Voice ID starts listening to the audio to create a voiceprint\. The voiceprint that is created this time is used for authentication purposes so Voice ID can compare if the caller had been enrolled previously\.

1.  It compares the caller's current voiceprint with the stored voiceprint associated with the claimed identity\. It returns a result based on the **Authentication threshold** property you configured in the [Set Voice ID](set-voice-id.md) block\.

1. After it evaluates the speech, it returns the message **Authenticated** if the voiceprints are similar\. Or it returns one of the other statuses\.

1. The contact is then routed down the appropriate branch by the [Check Voice ID](check-voice-id.md) block\.