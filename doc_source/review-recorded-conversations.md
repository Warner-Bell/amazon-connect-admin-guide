# Review recorded conversations between agents and customers using Amazon Connect<a name="review-recorded-conversations"></a>

Managers can review past conversations between agents and customers\. To set this up, you need to [set up recording behavior](set-up-recordings.md), assign managers the appropriate permissions, and then show them how to access the recorded conversations\. 

**When is a conversation recorded?** A conversation is recorded only when the contact is connected to an agent\. The contact is not recorded before then, when they are connected to the IVR\. If the call is transferred externally, the call recording stops when the agent drops from the call\.

**Tip**  
When call recording is enabled, the recording is placed in your S3 bucket shortly after the contact is disconnected\. Then the recording is available for you to review it using the steps in this article\.   
You can also access the recording from the customer's [contact record](sample-ctr.md)\. The recording is available in the contact record, however, only after the contact has left the [After Contact Work \(ACW\) state](metrics-agent-status.md#agent-status-acw)\.

**How do I manage access to recordings?** Use the **Recorded conversations \(unredacted\)** security profile permission to manage who can listen to recordings, and access the corresponding URLs that are generated in S3\. For more information about this permission, see [Assign permissions to review recordings of past conversations](assign-permssions-to-review-recordings.md)\.

## Review recordings/transcripts of past conversations<a name="review-recordings-and-transcripts"></a>

These are the steps that a manager does to review past recordings/transcripts of conversations\.

1. Log in to Amazon Connect with a user account that has [permissions to access recordings](assign-permssions-to-review-recordings.md)\.

1. In Amazon Connect choose **Analytics and optimization**, **Contact search**\. 

1. Filter the list of contacts by date, agent login, phone number, or other criteria\. Choose **Search**\.
**Tip**  
We recommend using the **Contact ID **filter to [search for recordings](search-recordings.md)\. This is the best way to ensure you get the right recording for the contact\. Many recordings have the same name as the contact ID, but not all\. 

1. Conversations that were recorded have icons in the **Recording/Transcript** column, as shown in the following image\. If you don't have the appropriate permissions, you won't see these icons\.  
![\[The voice recording icons play, download, and delete on the Contact search results page.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/recording-icons.png)

1. To listen to a recording of a voice conversation, or read the transcript of a chat, choose the **Play** icon, as shown in the following image\.  
![\[The voice recording icons play icon on the Contact search results page.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/play-recordings.png)

1. If you choose the play icon for a transcript, it appears, as shown in the following image\.   
![\[A sample chat transcript.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/sample-chat-transcript.png)

## Pause, rewind, or fast\-forward a recording<a name="pause-rewind-fastforward-recording"></a>

Use the following steps to pause, rewinder, or fast\-forward a voice recording\. 

1. On the **Contact search** results, instead of choosing the **Play** icon, choose the contact ID to open the contact record\.  
![\[The location of the contact ID that you need to choose.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/recordings-contactid.png)

1. On the **Contact record** page, there are more controls to navigate the recording, as shown in the following image\.  
![\[The contact record page, additional controls to listen to the recording.\]](http://docs.aws.amazon.com/connect/latest/adminguide/images/recording-pause-rewind-fastforward.png)

   1. Click or tap to the time you want to investigate\.

   1. Adjust the playing speed\.

   1. Play, pause, skip backwards or forwards in 10 second increments\.

## Troubleshoot problems pausing, rewinding, or fast\-forwarding<a name="problems-pause-rewind-fastforward-recording"></a>

If you are unable to pause, rewind or fast\-forward recordings on the **Contact search** page, one possible reason could be that your network is blocking HTTP range requests\. See [HTTP range requests]( https://developer.mozilla.org/en-US/docs/Web/HTTP/Range_requests) on the MDN Web Docs site\. Work with your network administrator to unblock HTTP range requests\.