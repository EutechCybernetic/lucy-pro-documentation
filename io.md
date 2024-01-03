

# Working with IoT and Real-Time Systems

Lucy is particularly well-suited to integrating control systems, IoT devices and other real-time systems into your work flows.

It has out of the box support for MQTT and has connectors available for all kinds of control system protocols.

{% hint type="note" %}
    Contact Eutech for a list of available connectors that you can deploy. {% endhint %}


## MQTT Connector
Your Lucy account comes with an Mqtt Broker allocated to it by default.
You can always change it to a different server if you choose.
You can view your Mqtt Broker settings from your Lucy dashboard.
From there, you can edit the broker settings.
Note that even though we configure a mqtt-over-websocket server as well, that isn't currently used by Lucy.
Its for your own use for testing.

### Receiving MQTT messages in your model
You can build models that process MQTT messages in real-time. 
To do this, you need to setup a subscription that will receive MQTT messages on a topic and send them to Lucy as events.
Your model can then listen for these events and react to them.

To setup a subscription, , click on View All Subscriptions in the MQTT weblet on your dashboard, or go to the image:: images/gear.png
menu, go to Connectors and then choose MQTT.

Here you can view a list of all subscriptions, edit them and add a new one.
A subscription is made by defining an MQTT topic pattern to subscribe to, a Quality of Service, 
the name of the Lucy event to fire and deciding how to receive the message content.

#### MQTT Topic Pattern
This determines what topic to listen for to pick up messages.
You can use wildcards or any normal pattern specifier here.

{% hint type="seealso" %}
    MQTT Topic Patterns: https://www.hivemq.com/blog/mqtt-essentials-part-5-mqtt-topics-best-practices {% endhint %}

#### Quality Of Service
The MQTT protocol defines differnt qualities of service to determine how safely and robust the message delivery yes.
`Exactly Once` message delivery is the best but also most expensive.
You can decide what quality level you need based on your use case. If you aren't sure about this, select the `Not Sure` option.
Lucy will pick an appropriate value.

#### Event ID
This is the event that will be fired in Lucy when a message is received on a topic matching the given pattern.
You can fill in any name for your event.
If the event has not yet been [registered](eventsregister), it will automatically get registered.

{% hint type="seealso" %}
    [Event Stream and Event Handling](events.rst#eventhandling)  for more information on how to handle events. {% endhint %}


#### Content Type
You can tell Lucy how the message received in MQTT should be treated when sending as an event.

There are two options:

##### Text
With this option, the full message received by the MQTT broker is sent as a parameter called `Payload` along with the event.
In addition a parameter called `Topic` is sent as well, describing the actual topic that the message was sent to.

##### JSON Object
With this option, the message is parsed as a JSON object and individual key/value pairs from the JSON are sent as separate parameters along with the event.
This saves you from havin to process it as JSON within your Lucy action sequence.

{% hint type="note" %}
    If you're not sure about the payloads you might receive, its safe to send it as `Text` and then process it within Lucy. {% endhint %}


### Publishing to MQTT
Publishing messages on an MQTT topic is easy.
You can use the [MqttPublish](blocks.rst#mqttpublish-ref) block within any Lucy action sequence to publish a message on a given topic.


## Processing Real-Time Data
There are some useful Lucy blocks for processing real-time data.

Some of them are:

### [Deadband](blocks.rst#deadband-ref)
It's common for values from real-time systems to fluctuate slightly and jitter.
This block lets you filter out values unless they have changed by a significant amount.

For example, you may want to process a temperature reading only when it changes significantly.
This block will pass its input to the output pin only if the value changes sufficiently, OR a given time window has passed.


### [Set Value](blocks.rst#setinredis-ref)
Use this to store an arbitrary value against a key.
One useful use-case is storing a sensor's value against its id.
You can also set an expiry time so that if the value is stale, it will be removed.

You can use the corresponding [Get Value](blocks.rst#getfromredis-ref) block to read the value back.

### [PublishMessage](blocks.rst#publishmessage-ref)
Use this block to publish data on the real-time [Message Bus](messagebus.rst#messagebus).
You can make client apps that run on webpages, desktops or mobiles that can have data pushed to it in real-time using thhis block.