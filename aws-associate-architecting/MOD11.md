# Building Decoupled Architectures

What's this about?:
- Your architecture now supports loads of users, but if one part fails, it all fails
- You need to remove dependencies

So:
- Decoupled architecture
- Using Amazon SQS and Amazon SNS to create decoupled architectures

Coupled architectures:
- Have lots of interconnected parts
- Are hard to manage
- Are inflexible
- Increase greatly in complexity as new components are added

How can you achieve decoupling?
- Seperate out stuff into layers, and have those layers speak to common elements, such as a load balancer to communicate between each other

## Amazon SQS

It:
- Is a fully managed message queueing service
- Stores messages until they are processed and deleted
- Acts as a buffer between senders and recievers
- Has dead-letter-queue support
- Visibility timeout:
  - It is the period of time that a message is 'invisible' to the rest of your application
- Has long or short polling:
  - Long polling is a method of retrieving messages
  - It will only return a response when a message arrives in the message queue
  - Short polling will return immediately, whether there is a message or not

With SQS, you can:
- Use asynchronous processing to get your responses quickly from each step
- Handle performance and service requirements by increasing the number of job instances
- Easily recover from failed steps since messages remain in the queue

There are two queue types:
- Standard
  - Messages are processed at least once
  - Nearly an unlimited number of transactions per second (TPS)
- FIFO
  - Messages are processed exactly once
  - Can be given in batches, of up to 10
  - Up to 300 messages per second
  - Theoretical maximum of 3000 per second (300 * 10)

Good and bad use cases:
- Good:
  - Service-to-service communication
  - Asynchronous work items
  - State change notifications
- Bad:
  - Selecting specific messages
  - Large messages (max 256kb)

## Amazon SNS (Simple Notification Service)

It:
- Matches publishers to subscribers
  - A publisher will post items to a 'topic' and all subscribers to that 'topic' will recieve a notification
  - This can be used to initiate a workflow off the back of an event

## Comparison

They:
- Have message persistence:
  - SNS: No
  - SQS: Yes
- Producers and consumers:
  - SNS: Publish/subscribe
  - SQS: Send/recieve
- Have delivery mechanism:
  - SNS: Push (passive)
  - SQS: Poll (active)
- Have distribution model:
  - SNS: (1 to *)
  - SQS: (1 to 1)


























