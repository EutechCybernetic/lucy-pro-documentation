


<a name='messagebus'></a>

# Message Bus
The Message Bus is a key component of Lucy for communicating with other models and external systems using a `publish/subscribe` interface.

You can publish a *message* to a specific *channel*.
A receiver can subscribe to one or more *channel*s to receive messages on them asynchronously.

The subscriber to messages could be in an external component, using the Lucy Connector SDK to subscribe to a channel. This makes the Message Bus an ideal system for sending commands to devices or external systems.

When your model needs to send an instruction to a device, it only needs to publish it as a message to a predefined channel that is subscribed to by the device's connector.

Using this mechanism, it is possible to talk to externally connected devices without having to open up the firewall in the listener.

{% hint style="info" %}

    One thing you need to be aware of: The publish/subscribe mechanism is asnychronous, using a fire-and-forget system. This allows for better scalability, but it also means you cannot directly receive a response to a message that is published. You will need a different mechanism for receiving responses from devices to specific messages. See [Design Patterns](designpatterns.md#designpatterns) for more information on how this can be achieved.

{% endhint %}

{% hint type="warning" %}
    Messages published on the message bus are ephemeral by default. This means, if a listener is not currently subscribed to a channel or is not listening for some reason (say, because of network connectivity issues), then they will not receive messages during that period of time. Messages are not stored and sent later - they are sent immediately to anyone who is actively listening. If you want more robust message handling, see below on using a messaging queue. {% endhint %}

<a name='mbpublish'></a>

## Publishing Messages
You can publish messages to a channel by using the [PublishMessage](blocks.md#publishmessage-ref) block in your action sequence. You need to specify a channel name and a message to send.
The message should be in text form. If you want to pass a `dictionary` then first serialize it to JSON using the [Serialize JSON](block-source.raw.md#tojson-ref) block.

<a name='mbsubscribe'></a>

## Subscribing to a channel
See the Lucy Connector SDK documentation for how your component can subscribe to a channel.
|Model| action sequences currently cannot subscribe to a channel. Use events to communicate with models.

## Message Queues
The Message Queue provides a more robust system for publishing messages. Messages are permanent and persist until they are explicitly removed. You have control over when a message is removed, allowing you to make better guarantees about your system. You can also set an optional expiry for messages. There is also a global configuration in iviva to set a default expiry for all messages.

{% hint style="info" %}

    Setting a default timeout for all queued messages requires administrative access.

{% endhint %}


<a name='mbqpublish'></a>

### Publishing Messages
Publishing messages on a queue works the same way it does for ephemral messages. The block for publishing to the queue is different - [PublishMessageToQueue](blocks.md#objectaction:System:PublishMessageToQueue-ref) - but takes the same inputs with an additional expiry input that specifies the lifetime of the message.

When a message is published onto a queue for a given channel, it persists there until it is removed. The message is also pushed down to all subscribers.
Subscribers also have the option of retrieving messages from the queue at any time.

<a name='mbqsubscribe'></a>

### Subscribing to a channel
There are two ways in which a subscriber can retrieve messages from the queue for a given channel:

1. Remove messages from the queue - The subscriber can choose to atomically remove messages from the queue and retrieve them. The subscriber should specify how many items to retrieve. At most, that many items are retreived and removed from the queue.

2. Lock messages on the queue - The subscriber can choose to atomically lock messages on the queue and return them. The items remain on the queue but are locked and will not be retrieved again by any other subscriber. The messages get unlocked automatically after `10` minutes, at which point, other subscribers may retrieve them. The subscriber locking items in the queue is responsible for manually issuing a command to delete the item from the queue once the subscriber is done processing it.

{% hint style="info" %}

    - Use **Message Queues** when you need stronger message delivery guarantees at the cost of performance
    - Use **Message Bus** when you need faster delivery and simplicity and can handle potentially lost messages (for example - real-time values are not important a few minutes after they are published, so there is no requirement to be able to see older values for processing data)

{% endhint %}

{% hint style="seealso" %}

    [Lucy Connector SDK](connectorsdk.md#connectorsdk) - for more information on retreiving and removing items from the message queue

{% endhint %}