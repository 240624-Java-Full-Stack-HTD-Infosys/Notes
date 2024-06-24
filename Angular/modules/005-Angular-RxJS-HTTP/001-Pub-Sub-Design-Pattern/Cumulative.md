# Cumulative for the  Pub Sub Design Pattern
<details><summary>Prerequisites and Learning Objectives</summary>

# Prerequisites

- Sound knowledge of HTML, CSS, and JavaScript.
- The Basic idea of the MVC (Model-View-Controller) architecture.
- Basic knowledge about TypeScript.


# Learning Objectives

- To define Publisher/Subscriber design pattern


</details>
<details><summary>Description</summary>

# Description


- The pub/sub (Publisher/Subscriber), is an architectural design pattern in which publisers and subscribers communicate with one another.
- A message handeller acts as a middleware between the publishers and subscribers.
- Messages (events) are sent out by the host (pubisher) to the message queue (event channel), subscribers join the message queue.

The following picture explains the pub/sub design pattern.

![Pub/Sub](/modules_new/resources/PubSub.PNG)


**Pro's of Pub/Sub design pattern:**

- Scales with multiple receivers
- Great with microservices
- Loose Coupling
- Works while client is not running


**Con's of Pub/Sub design pattern:**

- Message delivery issues
- Complex

</details>
<details><summary>Real World Application</summary>

# Real World Application

Consider a user uploading a video in youtube.

![Youtube Pub/Sub model](/modules_new/resources/PubSubExample.PNG)

1. The upload service will take the video and sends response to user once the video is uploaded and after that the user can disconnect.
2. The upload service will publish the raw mp4 video to th message queue.
3. The compress service is subscribed to Raw mp4 video and will receive raw mp4 and process it and publishes compressed video.
4. The format service is subscribed to compressed video topic and it publishes theh 480p, 1080p and 4k video.
5. The notification service is subscribed to 4k video and sends the notification in youtube.
</details>
<details><summary>Summary</summary> 

# Summary

- The pub/sub (Publisher/Subscriber), is an architectural design pattern in which publisers and subscribers communicate with one another using a middleware called event channel or message queue.
- Pub/Sub design pattern is an advancement over the request/response design pattern.
</details>
<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)</details>
