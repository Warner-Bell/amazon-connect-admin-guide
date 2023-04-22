# Search for contacts<a name="contact-search"></a>

## Important things to know<a name="important-contact-search"></a>
+ You can search for contacts as far back as two years ago\.
+ Amazon Connect returns results for completed contacts\. If an agent is still doing After Contact Work \(ACW\) on a contact, for example, that contact is not considered closed and won't be returned in the search results\.
+ The search results for a given query are limited to the first 10K results returned\.
+ When you filter by Contact ID, only results for that specific contact will be returned and other criteria are ignored\. For example, say you search for Contact ID 12345 and agent login Jane Doe\. Results for Contact ID 12345 will be returned regardless of whether Jane Doe was the agent\.
+ You cannot search for multiple contact IDs at the same time\.

## Key search features<a name="key-search-features"></a>
+ [Search by custom contact attributes](search-custom-attributes.md) \(user\-defined attributes\)\.
+ Search a time range up to 8 weeks\.
+ Multi\-select for filters such as agent names, contact queues, contact flows, and more\. 

  This feature is available only for searches with a date range that starts November 2, 2020, or later, when the feature was released\. If you search for contacts that occurred before November 2, 2020, you will be prompted to ensure only one value is selected for each filter mentioned above\. 
+ Filters for [Contact Lens for Amazon Connect](analyze-conversations.md)\. You can [search for Contact categories](search-conversations.md#contact-category-search) by specifying the full category name\. Choose to search using **Match any** or **Match all**\. For example, you can search contacts with both "category A" and "category B," or with either one of the two categories\.

  In the **Add filter** drop\-down box, the Contact Lens filters have **CL** next to them\. You can apply these filters only if your organization has enabled Contact Lens\.   
![\[The contact search page, the filters section, the filter dropdown menu.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/contact-lens-search-contact-category-1.png)

  If you want to remove the Contact Lens filters from a user's drop\-down list, remove the following permissions from their security profile: 
  + **Search contacts by conversation**: This controls access to the sentiment scores, non\-talk time, and category searches\.
  +  **Search contacts by keywords**: This controls access to the keywords search\.
  +  **Contact Lens \- speech analytics**: On the Contact Trace Record page, this displays graphs that summarize speech analytics\.
+ Filters for [Voice ID](voice-id.md)\. You can search for the Voice ID authentication and fraud detection status of contacts, if your organization has enabled Voice ID\. To access this functionality, on your security profile, you need **Analytics and Optimization**, **Voice ID \- attributes and search** \- **View** permission\.

  The following image shows the filters available to search Voice ID: **Authentication result**, **Fraud detection result**, **Speaker actions**\.  
![\[The filter dropdown menu, filters for Voice ID.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/voiceid-search-filters.png)

## Manage who can search for contacts and access detailed information<a name="required-permissions-search-contacts"></a>

Before users can search for contacts in Amazon Connect, or access detailed contact information, they need to be assigned to the **CallCenterManager** security profile, or have the following **Analytics and Optimization** permissions:
+ **Access metrics \- Access** \(Required\): Grants access to metrics data\.
+ **Contact search \- View** \(Required\): Grants access to the **Contact search** page, and the ability to search for contacts\.
+ **Restrict contact access** \(Optional\): Manage a user's access to results on the **Contact search** page based on their agent hierarchy group\.

  For example, agents who are assigned to AgentGroup\-1 can only view contact records for contacts handled by agents in that hierarchy group, and any groups below them\. \(If they have permissions for **Recorded conversations**, they can also listen to call recordings and view transcripts\.\) Agents assigned to AgentGroup\-2 can only access contact records for contacts handled by their group, and any groups below them\. 

  Managers and others who are in higher level groups can view contact records for contacts handled by all the groups below them, such as AgentGroup\-1 and 2\.

  For this permission, **All** = **View** since **View** is the only action granted\.

  For more information about hierarchy groups, see [Set up agent hierarchies](agent-hierarchy.md)\.
**Note**  
When you change a user's hierarchy group, it may take a couple of minutes for their contact search results to reflect their new permissions\.
+ **Contact Lens \- speech analytics**: On the Contact Record page for a contact, you can view graphs that summarize speech analytics: customer sentiment trend, sentiment, and non\-talk time\. 
+ **Recorded conversations \(redacted\)**: If your organization uses Contact Lens for Amazon Connect, you can assign this permission so agents access only those call recordings and transcripts in which sensitive data has been removed\.
+ **Recorded conversations \(unredacted\)**: If your organization isn't using Contact Lens, agents need **Recorded conversations \(unredacted\)** to listen to call recordings or view transcripts\. If desired, you can use **Restrict contact access** to ensure they only have access to detailed information for those contacts handled by their hierarchy group\. 
+ **Voice ID \- attributes and search**: If your organization uses Voice ID, users with this permission can search for and view Voice ID results in the **Contact detail** page\. 
+ **Users \- View** permission: You must have this permission to use the **Agent** filter on the **Contact search** page\.

By default, the Amazon Connect **Admin** and **CallCenterManager** security profiles have these permissions\.

For information about how add more permissions to an existing security profile, see [Update security profiles](update-security-profiles.md)\.

## How to search for a contact<a name="how-to-search-contacts"></a>

1. Log in to Amazon Connect with a user account that has [permissions to access contact records](#required-permissions-search-contacts)\.

1. In Amazon Connect choose **Analytics and optimization**, **Contact search**\.

1. Use the filters on the page to narrow your search\. For date, you can search up to 8 weeks at a time\.

**Tip**  
To see if a conversation was recorded, you need to be assigned to a profile that has **Manager monitor** permissions\. If a conversation was recorded, by default the search result will indicate so with an icon in the **Recording** column\. You won't see this icon if you don't have permission to review the recordings\.

## Additional fields: Add columns to your search results<a name="additional-fields"></a>

Use the options under **Additional fields** to add columns in your search results\. These options are not used to filter your search\.

For example, if you want to include columns for **Agent Name** and **Routing profile** in your search output, choose those columns here\.

**Tip**  
The **Is transferred out** option indicates whether the contact was transferred to an external number\. For the date and time \(in UTC time\) when the transfer was connected, see `TransferCompletedTimestamp` in the [ContactTraceRecord](ctr-data-model.md#ctr-ContactTraceRecord)\. 

## Download search results<a name="download-search-results"></a>

You can download up to 3,000 search results at a time\. 