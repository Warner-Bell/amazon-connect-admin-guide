# Emergency admin login<a name="emergency-admin-login"></a>

As a best practice, users assigned to the Amazon Connect **Admin** security profile should always use their Amazon Connect instance URL to login:
+ Log in to Amazon Connect at https://*instance name*\.my\.connect\.aws/\.

This method ensures the appropriate levels security\.

However, if there's an emergency, you can log in from the Amazon Connect console using your AWS account credentials\. For example, you may need to login in this way in the following situations:
+ You forgot your Amazon Connect administrator password and no other Amazon Connect administrators are around to reset it\.
+ Someone deleted the Amazon Connect **Admin** security profile by mistake\.

**To login for emergency access**

1. Make sure you have your AWS account credentials at hand and that you have the [required permissions](security-iam-amazon-connect-permissions.md#federations)\.

1. Open the Amazon Connect console at [https://console\.aws\.amazon\.com/connect/](https://console.aws.amazon.com/connect/)\.

1. If prompted to login, enter your AWS account credentials\.

1. Choose the name of the instance from the **Instance alias** column\.  
![\[The Amazon Connect virtual contact center instances page, the instance alias.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/instance.png)

1. In the navigation pane, choose **Overview**\.

1. Choose **Log in for emergency access**\.

   You aren't prompted for your credentials because you are federated in from the AWS console\.
**Important**  
For daily usage, we strongly recommend always using your instance URL to login\. The procedure provided in this article should only be used for emergency access when using the instance URL is not an option\.

**To log out**  
To log out of your instance, go to the title bar at the top of the screen and select the icon with the arrow \(**Log out**\) that appears next to your user name\.