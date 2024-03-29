


<a name='queues'></a>

# Queues
Lucy Queues allow you to build robust integrations that are fault tolerant and scalable.


There are two common scenarios where queues can be useful:

1. Transferring data from one system to another
2. Sending out commands to multiple systems (broadcasting messages via  webhook or connector).

In these scenarios, rather than directly triggering a data transfer or message broadcast from the source, you would put the item into a queue and have a separate task for processing items from the queue.
Using a queue as an intermediate store of data has several advantages:

1. The rate at which source data is generated can differ from the rate at which data is consumed or broadcast out.
2. Items processed from a queue can be configured to retry failed executions.
3. You can monitor the queue through the user interface and keep track of progress


To use queues as part of your integration, you can use the Queue block.


The Queue block is under the list category. 
This will look similar to a repeater block in that it will have an input side and the output side will have a link to an [action](actions.md#actions) block. 

When the block receives inputs, it will put the input into a queue. 
There will be a separate task to read items from the queue and execute the linked action, passing each item as a parameter to it.

## Configurations



|Label|Description|
|--|--|
|Input 01|This is the default input pin. You can remove this add and add other inputs as you require.|
 

{% hint type="note" %}
    You can add multiple inputs here. {% endhint %}



|Label|Description|
|--|--|
|Output|This is linked to a [action](actions.md#actions) block. The linked action will execute to process each item in the queue. Any data returned from the linked action (using a|
|Queue Id|This will return a unique id for the item that got queued.
{% hint type="note" %}
You are unable to add output pins to the queue block but You can add output pins to action block. {% endhint %}|
 

{% hint type="note" %}
    When adding output pins to the action block, make sure that names of the output pins are identicle to the input pins in the queue block {% endhint %}

