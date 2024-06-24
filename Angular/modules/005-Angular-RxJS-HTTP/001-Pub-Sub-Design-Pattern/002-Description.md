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

