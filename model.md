

<a name='models'></a>

# Models
Models are the central component of Lucy.

|Mms| are where you model your business objects, define attributes and orchestrate workflows and other logic.

Models contain attributes as well as action sequences that you can define.

Typically, each *type* of business object in your organization will have its own model in Lucy.

For example, if you wish to model employees in your organization, then you may choose to create a model called **Employee**.

However, if you find that you need to manage *Managers* and *Technicians* in your organization in different ways, then you may want to create two models instead - **Manager** and **Technician**

Models are not just used to manage metadata for physical objects or people. They are also used to manage workflows and any abstract entities you want to include to help manage your workplace better.

A workflow to turn off all lights after 6pm could be handled by defining a model.
A relationship between a supervisor and the location she is supervising can also be defined and managed by a model.

Other examples of models include:

- **Asset** - *Model all assets in your organization*
- **AccessCardProvisioning** - A model to manage the workflows for provisioning new access cards into your system

{% hint type="note" %}
    There are many other types of models you may create. We'll visit more of them in the section on Design Patterns {% endhint %}

<a name='attributes'></a>