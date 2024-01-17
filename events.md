

<a name='eventhandling'></a>

# Event Stream and Event Handling
The Lucy Event Stream is a powerfull component of the overall architecture.

The event stream lets devices, objects and external systems pump events continuously into Lucy to be reactively processed, asynchronously by models within lucy.

A single event could be processed by many Lucy models, or none at all.

Using events, you can decouple the source that is triggering events, from the receivers that will process them. This lets you build device connectors that can raise events without having to worry about how or who will consume it

Events may be raised to signal abnormal conditions, like a fire alarm.

They can also be used to periodically send sensor readings or other data to the server.

iviva applications raise events whenever any important interactions occur in the system. For example, creating a work order, updating the details of a location all trigger events.

## Event Structure
Events consist of the following pieces of information:



|Field|Description|
|--|--|
|Event ID|A unique identifier for the event being raised|
|LocationKey|The iviva location from which the event was triggered|
|Payload|An event payload, in JSON format|
 

The `EventID` field is the most important of these. The `EventID` uniquely identifies this type of event and is the name used to subscribe to events.

## Event ID Naming Convention
The EventID can be anything unique but we recommend using the url path format:

```

    /object-type/modifier
    /object-type/subobject-type/modifier

```

Some examples of events:

```

    /WorkOrder/created
    /Asset/updated
    /sensor/reading
    /ibms/alarm

```

<a name='eventsregister'></a>

## Registering Events
Events can be registered in the system in order to make them easily discoverable for use in models.

To view or register events in the system, go to

```

    http://<lucyurl>/Apps/System/eventsregister

```

From here, you can search for and view a list of all events that have been registered. Click on any of one of them to update it.

Click the `Register New Event` link to register a new event.

When registering a new event or updating an existing event, you need to specify the EventID, a description and a JSON block describing the typical payload it expects.

This JSON block should be an object with keys that represent the payload parameters. The values contain a description of each of the fields.

For example:

```

    {
        "asset":"The asset that is sending the reading",
        "value":"The actual value of the reading",
####         "unit":"The units in which the reading is being sent"

```

{% hint style="info" %}

    It is not required to register all events in the system. This is a convenience to make it easy to discover what events are available for subscription. Ad-Hoc one-time events do not need to be registered. However, it is recommended that all connectors that raise events register them in the system.

{% endhint %}


## Triggering Events

## Handling Events
Events can be processed in Lucy by using an [Event Start](block-source.raw.md#eventstart-ref) block.
Placing one of these blocks in your action sequence designer will automatically allow that model to start subscribing to the specified event.

Events can be triggered in three different ways:

1. On the model
2. On an model instance of the model.
3. By creating a new model instance of the model.


## Triggering on the Model
To make an event trigger on the model, when selecting an [Event Start](block-source.raw.md#eventstart-ref) block, in the properties panel, select the `Run on model` option.

In this mode, the triggered event is execued directly on the model.

.. In this mode, the triggered event first creates a new instance of the model and
.. then executes the event trigger block in that newly instantiated model. (Any .. constructor blocks you have will run)

##### Sequence of Items
1. Event engine picks up event
2. Event engine looks for any *models* (not instances) that contain the corresponding event trigger
3. For each model found

  1. Event Engine triggers the sequence on that model


<a name='eventtriggernewinstance'></a>

## Trigger a new Instance
In this mode, a new model instance is created from the model each time the event triggers. The rest of the blocks execute on the newly created model instance.

To make an event trigger a new model instance, when selecting an [Event Start](block-source.raw.md#eventstart-ref) block, in the properties panel, select the `Trigger new Instance` option.

A common use case for this is if you define a model that extends or shadows another object and want to create an instance of this model whenever that object gets created.
In this case, you would listen to the object's `created` event and then trigger the event on a new instance of the model.

{% hint type="note" %}
    Strictly speaking this mode can also be achieved by triggering the event on the model itself, and then calling an action that has *Instantiate* set to true. However doing it this way eliminates many steps. {% endhint %}

##### Sequence of Items
1. Event engine picks up event
2. Event engine looks for any *models* (not instances) that contain the corresponding event trigger
3. For each model found

  1. Event Engine initiates a new instance of that model
  2. Event Engine runs the constructors for that model
  3. Event Engine triggers the sequence


## Triggering on Instance
In this mode, the event engine looks for any **instances** that have attributes correlating with the event and then executes sequences on those instances.

To make an event trigger an existing model instance, when selecting an [Event Start](block-source.raw.md#eventstart-ref) block, in the properties panel, select the `Run on Instance` option.

When configuring correlation, parameters from the event are matched to values of attributes.
If all such correlations match, then the instance is picked up for execution.

##### Sequence of Items

1. Event engine picks up event
2. Event engine looks for any *instances* that contain the corresponding event trigger
3. For each instance that was found
  1. Event engine examines the correlations set on that event in that instance and matches the attribute values of that instance against event parameter values
  2. If all correlations match, that action sequence in that instance is triggered by the event engine