# Flow block definitions<a name="contact-block-definitions"></a>

Use flow blocks to create flows in the flow designer\. Drag flow blocks and drop them onto a canvas to arrange a flow\.

The following table lists all available flow blocks that you can use\. Choose any block name in the Block column for more information\.


| Block | Description | 
| --- | --- | 
| [Call phone number](call-phone-number.md)  | Initiates an outbound call from an outbound whisper flow\. | 
| [Amazon Connect Cases](cases-block.md)  | Gets, updates, and creates cases\.  | 
|  [Change routing priority / age](change-routing-priority.md)   |  Changes the priority of the contact in queue\. You may want to do this, for example, based on the contact's issue or other variable\.  | 
|  [Check call progress](check-call-progress.md)   |  Engages with the output provided by an answering machine, and provides branches to route the contact accordingly\. This block works with outbound campaigns only\.  | 
|  [Check contact attributes](check-contact-attributes.md)   |  Checks the values of contact attributes\.  | 
|   [Check hours of operation](check-hours-of-operation.md)  |  Checks whether the contact is occurring within or outside of the hours of operation defined for the queue\.  | 
|   [Check queue status](check-queue-status.md)   |  Checks the status of the queue based on specified conditions\.  | 
|   [Check Voice ID](check-voice-id.md)   |  Branches based on the enrollment status, voice authentication status, or status of detection of fraudsters in a watchlist of the caller returned by Voice ID\.  | 
|   [Check staffing](check-staffing.md)   |  Checks the current working queue, or queue you specify in the block, for whether agents are available, staffed, or online\. Staffed availability could be on call, or after contact work status\.  | 
|   [Create task](create-task-block.md)   |  Creates a new task, sets the tasks attributes, and initiates a contact flow to start the task\. To learn more about Amazon Connect Tasks, see [Concepts: Tasks in Amazon Connect](tasks.md)\.   | 
|   [Customer profiles](customer-profiles-block.md)   |  Enables you to retrieve, create, and update a customer profile\.  | 
|  [Disconnect / hang up](disconnect-hang-up.md)  |  Disconnects a contact\.  | 
|   [Distribute by percentage](distribute-by-percentage.md)   |  Routes customers randomly based on a percentage\.  | 
|   [End flow / Resume](end-flow-resume.md)   |  Ends the current flow without disconnecting the contact\.  | 
|   [Get customer input](get-customer-input.md)   |  Branches based on customer intent\.  | 
| [Get queue metrics](get-queue-metrics.md) | Retrieves real\-time metrics about queues and agents in your contact center and returns them as attributes\. | 
|  [Hold customer or agent](hold-customer-agent.md)  |  Places a customer or agent on or off hold\.  | 
|  [Invoke AWS Lambda function](invoke-lambda-function-block.md)  |  Calls AWS Lambda, optionally returns key\-value pairs\.  | 
|  [Invoke module ](invoke-module-block.md)  |  Calls a published module\.  | 
|  [Loop](loop.md)  |  Loops through, or repeats, the **Looping** branch for the number of loops specified\.  | 
|  [Loop prompts](loop-prompts.md)  |  Loops a sequence of prompts while a customer or agent is on hold or in queue\.   | 
|   [Play prompt](play.md)  |  Plays an interruptible audio prompt, delivers a text\-to\-speech message, or delivers a chat response\.  | 
|   [Set callback number](set-callback-number.md)   |  Sets a callback number\.  | 
|   [Set contact attributes](set-contact-attributes.md)   |  Stores key\-value pairs as contact attributes\.  | 
|  [Set customer queue flow](set-customer-queue-flow.md)  |  Specifies the flow to invoke when a customer is transferred to a queue\.  | 
|   [Set disconnect flow](set-disconnect-flow.md)   |  Sets the flow to run after a disconnect event\.  | 
|   [Set hold flow](set-hold-flow.md)   |  Links from one flow type to another\.  | 
|   [Set logging behavior](set-logging-behavior.md)   |  Enables flow logs so you can track events as contacts interact with flows\.  | 
|   [Set Voice ID](set-voice-id.md)   |  Sends audio to Amazon Connect Voice ID to verify the caller's identity and match against fraudsters in watchlist, as soon as the call is connected to a flow\.   | 
|   [Set recording and analytics behavior](set-recording-behavior.md)  |  Sets options for recording conversations\.  | 
|  [Set voice](set-voice.md)   |  Sets the text\-to\-speech \(TTS\) language and voice to be used in the flow\.  | 
|   [Set whisper flow](set-whisper-flow.md)  |  Overrides the default whisper by linking to a whisper flow\.  | 
|   [Set working queue](set-working-queue.md)   |  Specifies the queue to be used when **Transfer to queue** is invoked\.  | 
|  [Show view](show-view-block.md)  | Configures UI based workflows that you can surface to users in front end applications\. | 
|  [Start media streaming](start-media-streaming.md)  | Starts capturing customer audio for a contact\. | 
|  [Stop media streaming](stop-media-streaming.md)  | Stops capturing customer audio after it is started with a **Start media streaming** block\. | 
|   [Store customer input](store-customer-input.md)   |  Stores numerical input to a contact attribute\.  | 
|   [Transfer to agent \(beta\)](transfer-to-agent-block.md)  |  Transfers the customer to an agent\.  | 
|   [Transfer to flow](transfer-to-flow.md)  |  Transfers the customer to another flow\.  | 
|   [Transfer to phone number](transfer-to-phone-number.md)  |  Transfers the customer to a phone number external to your instance\.  | 
|   [Transfer to queue](transfer-to-queue.md)   |  In most flows, this block ends the current flow and places the customer in queue\. When used in a customer queue flow, this block transfers a contact already in a queue to another queue\.  | 
|   [Wait](wait.md)  |  Pauses the flow\.  | 
|   [Wisdom](wisdom.md)  |  Associates a Wisdom domain to a contact to enable real\-time recommendations\.  | 