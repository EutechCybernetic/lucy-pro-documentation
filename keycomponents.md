


# Key Components
In order to help you get to know Lucy better, it would help to understand the various components underlying the platform and how they work together.

## Model Designer
This is the tool you will use to design and create your models and action sequences in Lucy. This is a web-based visual interface to easily put together your solution.
See [Model Designer](model-designer) for more information.

.. UI Composer
.. ------------
.. This is a graphical tool to design your user interface elements that you will deploy as part of your Lucy development.
.. See [UI Composer](uicomposer) for more information.

## Orchestration Engine
This is the backend service responsible for executing the action sequences that you design and for storing data that you require

## Web Service Connector Toolkit
This is a configuration tool to let you define your own connectors to external systems.

{% hint style="seealso" %}

    [Web Service Connector Toolkit](connectortoolkit.md#connectortoolkit)

{% endhint %}

## Connector Gateways
These are gateways that allow Lucy to talk to other systems in your organization. These gateways run on external systems and act as a bridge between Lucy and other systems. These gateways are written using the Lucy Connector SDK.

{% hint style="seealso" %}

    [Lucy Connector SDK](connectorsdk.md#connectorsdk)

{% endhint %}

## Data Collections
You can define arbitrary data collections in Lucy and use it to store and query JSON documents.

{% hint type="seealso" %}
    
    [Data Collections](datacollections.md#datacollections) {% endhint %}

## Syncing Data
Lucy provides tools to scalably and robustly sync data.

You can make use of [Queues](queues.md#queues) to setup and monitor data to be synced.

.. Metadata Explorer
.. ------------------
.. This is a tool to visualize and navigate through the relationships between items in your system.
### .. It integrates both iviva applications as well as Lucy models.
.. See [Metadata Explorer](mde.md#mde) for more information.