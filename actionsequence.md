


<a name='actionsequences'></a>

# Action Sequences

## Triggering a sequence
Action sequences are triggered in three ways:

* Action Start Blocks
* Event Trigger Blocks


## Using Blocks
In |Lucy|, blocks are the individual components that make up a action sequence.
Each block usually does a small and very specific task.
Each block has input and output pins.
When a block receives data on its input pins, it does its work and then writes data to its output pins. |Lucy| then takes that data and feeds into the inputs of any other blocks that have connections to the output pins of the previous block.

You can visually build your action sequence by dragging and dropping blocks into the work area and then connecting the outputs of one block to the inputs of another. In this way you can describe the flow of your logic.

Some blocks are used for simple logical reasoning (`equals`, `greater`,`lessthan` etc...).

Others do much more complex pieces of work like adding a weblet to a dashboard, or making an http request to another service.

|Lucy| comes with a large collection of blocks to do many tasks.
In addition, |Lucy| can be extended by custom blocks published from a connector. You can also enhance lucy by building a library of your own blocks.

See [shareactions](shareactions) for more information on how to build up a library of your own re-usable blocks.


## Specifying Inputs
Inputs to blocks can be specified in two ways:

1. Directly connecting the output from another block into the input of this one
2. Explicitly setting a hard-coded value for a specific input.

To connect the output of one block to the input of another, simply drag the output pin of one block towards the input pin of another. When you drag the pin over the input of another block, if that block is able to accept this input, it will grow in size. At that point, you can drop the connection there to make it permanent and complete.

<figure><img src=' animations/connect-blocks.gif'></figure>

You can also explicitly specify the value for an input.
Simply select the block and then enter a value for that pin in the input pin's textbox in the Properties Panel.

.. .. image:: animations/specify-inputs.gif

### Variable inputs
It's possible for some blocks to allow a variable number of user-defined inputs.
For example, the |callaction| block lets you specify what inputs to pass to the action being called. In that case, use the `Add Input Parameter` link in the Properties Panel to add a new input pin. Click the image:: images/trash.png icon next to the pin in the Properties Panel to delete that pin.

{% hint type="warning" %}
    When you delete a pin, all the connections that go into that pin from other blocks are automatically deleted. {% endhint %}

## Specifying Outputs
Each block usually has a fixed set of output pins.
In some cases, it is possible to speciy a variable number of outputs.
For example, the |callaction| block lets you explicitly extract parameters from the action result as separate pins to be used.
For blocks that support multiple outputs, click the `Add Output Parameter` link in the Properties Panel to add a new output pin.
Use the image:: images/trash.png icon to delete an output pin.

{% hint type="warning" %}
    Just like with inputs, when you delete an output pin, it removes all connections that go out from it. {% endhint %}


<a name='dataflow'></a>

## Flow of Data and Execution

    *This section explains how data flows through the execution path and how the execution path is determined.*

Each execution path starts at one of the triggering blocks (`ActionStart`, `EventTrigger`, `Initiate`) and follows any connected output pins from there.

The basic rules for determining when a block is executed are as follows:

1. Each block is executed exactly once in a sequence
  * If the block appears multiple times during execution of a sequence, the block is **not** executed the second time.

2. Each block is executed only after its *connected* inputs have been written to.
  1. It doesn't matter what value is written (`null`, `0`, empty string are all valid values). Just that something should be written
  2. If a block is in the current execution path and not all of its connected pins have been written (possibly because the connecting block has not been executed yet) then execution of that block is deferred and that line of execution is halted at that point.
  It will later be revisited.

3. The order in which the connections from output pins is followed is undetermined. *(For example, You will not be able to assume that pins at the top of the block execute before pins at the bottom)*

In psuedo code, the execution can be considered to run roughly like this:

```

      def executeBlock(block)
        # do the work for that block
        for pin in block.outputPins
          block = pin.getConnectedBlock()
          if block.allInputsWritten()
            block.Execute()
          else
            block.defer()

```

    executeBlock(startingBlock)
    for block in deferredBlocks:
      executeBlock(block)


So execution continues along until it reaches a block that cannot be executed (because its input pins have not been written to yet) and so the block's execution is deferred, and that execution line is finished. The next line is started.
Once all lines are done, the deferred blocks are re-visited (in case some of their dependencies have now been written by other execution lines).

If the system determines that a block can never be executed (because some of its inputs can never be written) the block is marked as *unreachable*.

When executing from the `Test` tab of the model or when looking at the event engine output on a console, it prints out a list of blocks that were determined to be unreachable.

Unreachable blocks are normal and occur often in action sequences. For example, the `False` branch of an `Equals` block may be unreachable if the condition evaluated to `true.`