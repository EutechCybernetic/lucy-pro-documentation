

# Model Instances
Alright, so you have a model and it represents something important in your business - lets say, an Asset.
But you have thousands of assets in your organization. How does your model represent each and every one of those?

You need to deploy copies of your model - specifically, one for every *thing* [#]_ that you have


These copies are what we call |instances|.

They are special in that they all share the set of attributes defined in the model. However, the *value* for each of those attributes may be different for each model instance.

You can think of models and |instances| as being like a template for a document and the actual document itself.

You first define your template, and then make multiple documents out of that template.

So if you have 23,000 assets in your system, you need to create 23,000 |instances| of your **Asset** model.

All of them will share the same action sequences and the same set of attributes, however the actual values for attributes will differ from model instance to model instance.

.. rubric:: Footnotes

.. [#] that's a technical term

<a name='instanceattrs'></a>

## Attributes of |instances|
Along with inheriting the attributes of the model from which the model instance was created, each model instance also has a few special attributes:



|Attribute|Description|
-----------------------
|Name|This is a display name for the model instance being created. It is shown in search results and labels. This defaults to the name of the model. The |SetName| block can be used to explicitly set it to something more useful.|
|Description|A description of the model instance. Use of this will be depracated shortly.|
|IsActive|Set to `1` if the model instance is currently active. Otherwise set to `0`. All |instances| are active by default.|
|Key|This is a number that uniquely identifies a particular model instance|
 

{% hint style="warning" %}

    You can't explicitly define attributes in your model with names matching any of those special attributes above.

{% endhint %}

## Creating |instances|
There are several ways an instance of a model could be created:

1. By defining an [action](actions.md#actions) using an [Action Start](block-source.raw.md#actionstart-ref) block with the mode set to [Trigger new Instance](actions.md#actiontriggernewinstance). Then, calling this action on a model will automatically create a new instance of the model and run the action sequence for that action on this new instance.

2. Creating an instance by listening to an incoming [event](events.md#eventhandling). The [Event Start](block-source.raw.md#eventstart-ref) block must be set to [Trigger a new Instance](events.md#eventtriggernewinstance) to make it trigger a new instance of the model.

3. By invoking the instance creation dialog in a user interface.

    1. This can be done by clicking the *Create New Instance* link in the side bar of the model designer.
    2. If you define an extension attribute in your model, then from that extension's interface, you can click the |mapextension| icon to create a new instance of the model.

{% hint type="note" %}
    Probably the most common way you will create an instance is by using an action with the mode set to [trigger a new instance](actions.md#actiontriggernewinstance). This action can, in-turn be bound to some custom user interface that you build and present to the user. {% endhint %}

<a name='deactivateinstance'></a>

## Removing |instances|
You can disable or *deactivate* an instance of a model from the instance's details screen.

There are three ways to deactivate an instance:

    1. From the instance details screen, click on the **Deactivate** link in the sidebar to deactivate the instance.
    2. Use a |deactivate| block in your action sequence to deactivate the current instance
    3. Call the [deactivate()](es6javascript.md#jsdeactivate) function in a |javascript| block to deactivate an instance.

Deativating an instance does not permanently remove it from the system. It sets the IsActive status to `0`.

Deactivated instances can still responed to actions and details about them can be viewed.
However

1. They do not respond to event triggers
2. By default, they do not show up in the search page for that model, unless you specifically enable the *Include inactive items* filter.

{% hint type="warning" %}
    The system will periodically flush out inactive instances, so do not expect them to always be present. If you need some way of marking an instance as not valid but still want to see it in the system, then define your own custom attribute for this and as a convention, set its value to `1` or `0` to mark it as valid or invalid. {% endhint %}

{% hint type="note" %}
    When composing a [data source](datasources.md#datasources) to list out instances, you almost always want to include a filter to remove inactive instances. Add the IsActive attribute to the datasource and set its value to `1` under the *Conditions* section. {% endhint %}

## Instance Dashboards
Each instance of a model can have a dynamic dashboard associated with it.
Use this dashboard to track information in real-time and get up to date information. These dashboards are self-assembling - you can use logic in your action sequence to determine what to show and when to show it.

{% hint type="seealso" %}
    [Instance Details Page](dynamicuis.md#instancedetailsui) {% endhint %}