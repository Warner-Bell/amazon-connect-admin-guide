# Browsers supported by Amazon Connect<a name="connect-supported-browsers"></a>

Before you work with Amazon Connect, verify that your browser is supported using the following table\. 


| Browser | Version | How to check your version | 
| --- | --- | --- | 
|  Google Chrome  |  Latest three versions  | Open Chrome and type chrome://version in your address bar\. The version is in the Google Chrome field at the top of the results\. | 
|  Microsoft Edge Chromium  |  Latest three versions  | Open Edge\. On the menu, choose **Help and feedback** and then choose **About Microsoft Edge**\. The version number is listed in the **About** section\.  | 
|  Mozilla Firefox  |  Latest three versions  | Open Firefox\. On the menu, choose the Help icon and then choose **About Firefox**\. The version number is listed under the Firefox name\. Please see [Issue with Firefox version 86](#browsers-firefox-issue)\.  | 
|  Mozilla Firefox ESR  |  Versions are supported until their Firefox [end\-of\-life date](https://support.mozilla.org/en-US/kb/firefox-esr-release-cycle)\. For details, see the [Firefox ESR release calendar](https://wiki.mozilla.org/Release_Management/Calendar)\.   | Open Firefox\. On the menu, choose the Help icon and then choose **About Firefox**\. The version number is listed under the Firefox name\.  | 

 For more requirements, see [Agent headset and workstation requirements for the CCP](ccp-agent-hardware.md)\.

## Browsers on mobile devices<a name="browsers-mobile"></a>

The Amazon Connect console, Contact Control Panel \(CCP\), and agent workspace do not support mobile browsers\. However, your agents can forward the audio portion of the call to their mobile device\. For instructions, see [Forward calls to a mobile device \(iPhone, Android\)](forward-calls-to-mobile-device.md)\.

## Issue with Firefox version 86<a name="browsers-firefox-issue"></a>

The following issue may occur if you embed the Amazon Connect Contact Control Panel \(CCP\) into your agent application and your users access the Amazon Connect CCP using the Firefox web browser with **Enhanced Tracking Protection** browser setting set to **Strict**\. 

An upgrade to Firefox, specifically Firefox non\-ESR version 86 released on February 23, 2021, introduced [Total Cookie Protection](https://blog.mozilla.org/security/2021/02/23/total-cookie-protection/) which modified cookie sharing behavior across sites for users with **Enhanced Tracking Protection** set to **Strict** \(Firefox defaults to **Standard**\)\. Users with this specific browser setting and version combination may be unable to access the Amazon Connect CCP when embedded in another application, preventing them from handling contacts\. 

To prevent impact to your users \(agents\), we recommend that your users do one of the following:
+ Confirm \(or set\) **Enhanced Tracking Protection** as **Standard** in their browser settings\. Users can do this by following instructions documented [here](https://support.mozilla.org/en-US/kb/enhanced-tracking-protection-firefox-desktop#w_adjust-your-global-enhanced-tracking-protection-settings)\. 
+ Do not upgrade their Firefox browser version to v86 or higher\. 
+ Use Google Chrome or Microsoft Edge to access the Amazon Connect CCP\. 