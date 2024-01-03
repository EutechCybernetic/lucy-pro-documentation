

<a name='actions'></a>

# Actions
Actions are the easiest way to build logic in your model. An action begins with an [Action Start](actionstart-ref) block and triggers a action sequence in your model.

Actions can take inputs and return outputs.
Every action has an `http` end point that can be used to call the action as a web service call.

Use actions to

- Encapsulate any fundamental logic in your model
- Create a re-usable action sequence that can be called by any other action sequence in any other model in your solution.
- Publish an API for your model so that external systems, mobile apps and user interfaces can interact with your solution


## Defining an action

Drag an [Action Start](actionstart-ref) block into the Action Sequence Designer to define a new action.

By default the block has a single output pin called `All Outputs`. This pin contains all the inputs that were received by the action. They are passed directly to the block's output.

{% hint type="note" %}
    A little confusing, but, the inputs that are sent to the action when it is triggered get passed along through the block and show up as output pins in the action start block, so that they can be easily read for use in the action sequence {% endhint %}


An action can accept multiple inputs. To individually extract each input, just add a new output pin with the name of the field to be extracted.
Select the [Action Start](actionstart-ref) block, then in the [Properties Panel](modeldesigner.md#propertiespanel) click the 'Add Output' link to add a new output parameter. Multiple output paramaters can be specified at once by providing them as a comma separated list.

These pins can then be connected to other blocks to kickstart your logic for your action.

Actions can run on either the model itself, or on an instance of a model.


## Modes of Execution
Action Start Blocks can execute in three modes:

1. Run on Model
2. Run on Instance
3. Trigger New Instance


### Run on Model
In this mode, the action is executed on the model directly.

{% hint type="note" %}
	When an action sequence is run on a model, you do not have access to instance-specific blocks like |attributeget|, |attributeset|, |currentitem|. {% endhint %}

	When executing a sequence on the model, the `GetAttribute` blocks return `null` and the `SetAttribute` block simply returns the value that was passed in without setting it anywhere.


### Run on Instance
In this mode, the action is run on an model instance of a  model.

To call an action on an instance of the model, an instance key must be passed.

Note that the |attributeget| and |attributeset| blocks (along with a few other related blocks) are only really valid in the context of an instance.


<a name='actiontriggernewinstance'></a>

### Trigger New Instance
In this mode, the action sequence must be called on the model (not the instance). Calling this action will trigger the instantiation of a new instance of the model, any constructor blocks (`Initialize` blocks) for that model will run, and then the rest of the action sequence will execute on the newly created instance.

#### Sequence of Items

1. Model is loaded
2. New instance of the model is created with empty attributes
3. `Initialize` blocks in the model are executed in the context of the newly created instance
4. Actual action sequence is executed in the context of the newly created instance


## Types of Inputs
One of the important things you need to decide is how your action will receive inputs, in what format, and how you plan on making use of it.

{% hint style="seealso" %}

    [publishapiinputs](publishapiinputs)

{% endhint %}

### Key/Value Pairs
The easiest and most common way to receive inputs is as sets of key/value pairs.
This is the easiest to work with and fits many use-cases. When your action receives inputs as key/value pairs then you can easily extract them:

Just add new output pins - one for each key/value pair and specify the `key` name as the name of the output pin.

Lucy will automatically extract the value from that key/value pair and feed it into that pin.

A list of all key/value pairs are available as a dictionary by reading the `All Output` pin.

{% hint type="seealso" %}
    [Dictionaries and Objects](datatypes.md#dictionaries) {% endhint %}

### Structured JSON
More complex inputs can be received as structured JSON.
A simple JSON dictionary can be parsed and accessed using a [Parse JSON](block-source.raw.md#fromjson-ref) block.

More complex structures can be parsed using a javascript block.

For example, the following structure

```

    {
        "locationName":"Building 1",
        "locationType":"Building",
        "assets": [
            {"id":"ASSET01","type":"AHU"},
            {"id":"ASSET02","type":"FCU"},
####### ######             {"id":"ASSET03","type":"Temperature Sensor"},

```

Can be parsed using the following javascript code inside a [Javascript](es6javascript-ref) block:

```

    var json = inputs.JSON;
    var obj = JSON.parse(json);
    var location = obj.locationName;
    var type = obj.locationType;

```

    var assets = [];
    for(var i=0;i<obj.assets.length;i++) {
#######         assets.push(obj[i]);


### Binary Data

{% hint type="seealso" %}
    [Working with Binary Data](datatypes.md#binarydata) {% endhint %}

## Calling an action

There are three ways an action can be called:

- From the action sequence of another action
- As a webservice api
- From a user interface

To call an action from a workflow, use a |CallAction| block.
Specify the inputs to this block and also specify what outputs it expects.
Fill in the model name and the action name, and optionally, the instance key if the action is being called on a specific model instance.

{% hint type="note" %}
    The model name and action name are specified as text configured in the block. The model instance key however can be specified with an input pin as it is highly unlikely that you will have a valid model instance key at the time of designing your model. {% endhint %}

{% hint style="info" %}

    If you mark your action as *Published* it will show up in the [library](library).
    From there, you can easily drag and drop the action into your action sequence and it will automatically be setup and ready to use with the required inputs, outputs and model/action names.

{% endhint %}

For publishing your action as an API to be consumed by an external service, see [Publishing an API](publishingapi.md#publishapi)


<a name='shareactions'></a>
## Publishing Actions
You can make your action public if you feel it is useful as a generic service for other models to use.
When you click the `Publish Action` checkbox in the property panel of the [Action Start](actionstart-ref) block, the action gets marked as public.
Public actions are available in the [shared library](sharedlibrary) in the [Model Designer](model-designer) and can be easily re-used in other action sequences.


## Restricting access to Actions
You can restrict access to actions and allow them to only be executed by authorized users. This can be done by assigning roles to the action.
See [Applying Roles to Actions](permissions.md#permsactions) for more information on how to do this.