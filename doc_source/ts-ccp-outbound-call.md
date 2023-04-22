# Problem using the CCP: Agents can't make an outbound call<a name="ts-ccp-outbound-call"></a>

The top reason most agents can't make outbound calls from the CCP is because their instance of Amazon Connect has not been set up to make outbound calls\. 

**To enable agents to make outbound calls**

1. Open the Amazon Connect console at [https://console\.aws\.amazon\.com/connect/](https://console.aws.amazon.com/connect/)\.

1. On the instances page, choose the instance alias\. The instance alias is also your **instance name**, which appears in your Amazon Connect URL\. The following image shows the **Amazon Connect virtual contact center instances** page, with a box a box around the instance alias\.  
![\[The Amazon Connect virtual contact center instances page, the instance alias.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/instance.png)

1. In the navigation pane, choose **Telephony**\.

1. To enable outbound calling from your contact center, choose **I want to make outbound calls with Amazon Connect**\.

1. Choose **Save**\.