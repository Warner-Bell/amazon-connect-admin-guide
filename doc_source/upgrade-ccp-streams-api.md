# I use the Amazon Connect Streams API<a name="upgrade-ccp-streams-api"></a>

**Note**  
The Amazon Connect Streams API remains the same between the earlier and latest versions of the CCP\. We recommend validating custom implementations built using the Amazon Connect Streams API when upgrading versions to ensure consistency in behavior\.

Use the following steps to upgrade to the latest CCP\. 

1. We recommend using the latest [Amazon Connect Streams API](https://github.com/amazon-connect/amazon-connect-streams)\. 

1. Update the URL associated with `initCCP()` from **/ccp\#** to **/ccp\-v2**\. For information about `initCCP()`, see [connect\.core\.initCCP\(\)](https://github.com/aws/amazon-connect-streams#initialization) in the Amazon Connect Streams API documentation on GitHub\.

1. Add your domain URL to the Approved origin list: 

   1. Log in to the [AWS Management Console](https://console.aws.amazon.com/console) \(https://console\.aws\.amazon\.com/console\) using your AWS account\. 

   1. Navigate to the Amazon Connect console\.

   1. Check that you're in the correct Region for your Amazon Connect instance\. Choose your instance\.  
![\[The Amazon Connect virtual contact center instances page, the alias of your instance.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/tutorial1-lex-custom-bot18.png)

   1. Choose **Application integration**, and then choose **Add origin**\.  
![\[The left navigation pane, application integration option, Add origin.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/upgradeccp-application-integration.png)

   1. Enter your domain URL\. All domains that embed the CCP for a particular instance to be explicitly added\. For more information, see [this article](https://github.com/amazon-connect/amazon-connect-streams/blob/master/Documentation.md#allowlisting) on GitHub\. 

      If you use Salesforce, you need to add the Salesforce domains to your allow list to prevent any issues with the CTI Adapter CCP functionality\. For detailed instructions, see the  [Amazon Connect CTI Adapter for Salesforce Lightning installation guide](https://amazon-connect.github.io/amazon-connect-salesforce-cti/docs/lightning/notices/) or the [Amazon Connect CTI Adapter for Salesforce Classic installation guide](https://amazon-connect.github.io/amazon-connect-salesforce-cti/docs/classic/notices/)\. 

## Verify your network settings<a name="upgrade-verify-network-settings"></a>

We highly recommend setting up your network to use [Option 1 \(recommended\): Replace Amazon EC2 and CloudFront IP range requirements with a domain allow list](ccp-networking.md#option1)\. 

Using this option helps Amazon Connect Support to quickly troubleshoot any issues you have\. Specifically, using **\*\.telemetry\.connect\.\{region\}\.amazonaws\.com** passes more metrics to our Support team to help with troubleshooting\. 

## Update your SAML URL to ccp\-v2<a name="update-saml-url"></a>

If you use SAML 2\.0 as your identity management system, be sure to update the destination in your relay state URL to **ccp\-v2**\. 

Change `destination=/connect/ccp` to `destination=/connect/ccp-v2`\.

For more information, see [Use a destination in your relay state URL](configure-saml.md#destination-relay)