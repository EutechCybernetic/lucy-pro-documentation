


<a name='testing'></a>

# Testing and Debugging
Lucy includes several tools to help you with testing and debugging your action sequences.


You can directly run your actions from the [Model Designer](model-designer) and view their output.

You can also use the Orchestration Debugger to step through your flows and examine their inputs and outputs at each stage.

## Testing Actions
You can test your action sequences by using the [execution panel](executionpanel) from the [Model Designer](model-designer).

Either click the 'Play' icon in the toolbar or double-click the action or event start block to bring it up.

In the panel you will be prompted to specify values for any inputs that the sequence requires. 

Hit the code/Execute button to run the sequence.
On the right you can see the output and any debug information as well.

The debug output shows any messages printed by the |debug| block and any other debugging information that Lucy added while executing the action.

If your action is marked to run on an instance, you will also be prompted (in the test bubble) to enter the code/Instance Key to use to run the action.

If any error occurred while executing the action, the output panel will turn orange and the error message will be shown there.

{% hint type="note" %}
    You can test actions without having to save them first! However, if your actions in turn call other actions via |callaction| blocks then those will execute on the older saved version of the action. {% endhint %}

{% hint type="note" %}
    When you test an event, only that specific sequence will be tested. All action sequences that subscribe to that event will not be triggered. {% endhint %}


## Debugging action sequences
Lucy comes equipped with a debugger for action sequences.
You can choose to turn on debugging for your action sequences.
To enable debugging, select the starting block of your action or event and check off the 'Debug' option.
After saving, debugging will be enabled.

When debugging is enabled, all executions of that action sequence are recorded. 
This includes information about all blocks that were executed, the sequence in which they were executed, the inputs and outputs to each block and the timing for its execution.
If the block generated any error, that will be captured as well.

{% hint type="warning" %}
    Because of the wealth of information recorded during debugging it's recommended that you keep debugging turned on while testing but turn it off during live usage -
    especially if your models are complex or need to execute quickly. {% endhint %}

You can access the debugger by clicking the Debug icon in the sidebar panel.

The first thing you will see is list of all executions that have happened in chronological order.
If anny of the executions generated an error, it will be highlighted in orange.

<figure><img src=' images/debugger.png'></figure>


When you click on an action, you are shown the sequence of execution of blocks.
For each item, the name of the block and the time it took to execute it is shown.
If the block generated an error, that item will be highlighted in orange.

You can use the arrows on top to step forward and backwards through the sequence to see how it executed.

You can also jump to a specific block by clicking on it.

When you select on a block in the sequence list, the block gets highlighted in the [staging area](stagingarea) with other blocks grayed out.
Below the block in the debugger, you can see all the inputs and outputs to the block as well as any error if one was generated.

The inputs and outputs section show the name of the input/output, a symbol representing the [data type](datatypes) of the value, and the actual value itself.
Depending on the [data type](datatypes) of the value, you may be able to click on the value to expand it and see it in detail.

<figure><img src=' images/debugger-action.png'></figure>



### Global Debug Log

From the debugger panel on the top right, you can shift to showing the global debug log.
This shows you a log of all debug statements that were logged by all models in your account.
You can log items here from your [action](actions) in two ways:

1. Use a [debug-ref](debug-ref)
2. From a javascript block, using code/lucy.log()


### Performance Implications
Because of the wealth of information recorded during debugging, it is recommended that you turn it off in production where you expect your action to get executed often and/or expect it to run without any latency.

### Privacy Implications
Please see [Privacy](privacy) for more information on the privacy implications of debugging.