
..
    NEW BLOCK: equals

<a name='equals-ref'></a>

## Equals
Compares if two inputs are equal. When matching, both inputs are converted to text and matched.
Comparisons are case-insensitive.
Input:Input 1:The first value to compare
Input:Input 2:The value to compare against
Output:True:Writes the first input to this port if the condition is met. Else, doesn't write anything
Output:False:Writes the first input to this port if the condition is not met. Else, doesn't write anything.


..
    NEW BLOCK: nequals

<a name='nequals-ref'></a>

## Not Equal
Compares if two inputs are not equal. When matching, both inputs are converted to text and matched.
Comparisons are case-insensitive.
Input:Input 1:The first value to compare
Input:Input 2:The value to compare against
Output:True:Writes the first input to this port if the condition is met. Else, doesn't write anything
Output:False:Writes the first input to this port if the condition is not met. Else, doesn't write anything.


..
    NEW BLOCK: ltd

<a name='ltd-ref'></a>

## Before
Checks if the first datetime occurs prior to the second date time.

Input:Input 1:The first value to compare
Input:Input 2:The value to compare against
Output:True:Writes the first input to this port if the condition is met. Else, doesn't write anything
Output:False:Writes the first input to this port if the condition is not met. Else, doesn't write anything.


..
    NEW BLOCK: gtd

<a name='gtd-ref'></a>

## After
Checks if the first datetime occurs after the second date time.

Input:Input 1:The first value to compare
Input:Input 2:The value to compare against
Output:True:Writes the first input to this port if the condition is met. Else, doesn't write anything
Output:False:Writes the first input to this port if the condition is not met. Else, doesn't write anything.


..
    NEW BLOCK: gt

<a name='gt-ref'></a>

## Greater
Checks if the first value is greater than the second value.
(Inputs are converted to floating point when compared)

Input:Input 1:The first value to compare
Input:Input 2:The value to compare against
Output:True:Writes the first input to this port if the condition is met. Else, doesn't write anything
Output:False:Writes the first input to this port if the condition is not met. Else, doesn't write anything.


..
    NEW BLOCK: lt

<a name='lt-ref'></a>

## Less
Checks if the first value is less than the second value.
(Inputs are converted to floating point when compared)

Input:Input 1:The first value to compare
Input:Input 2:The value to compare against
Output:True:Writes the first input to this port if the condition is met. Else, doesn't write anything
Output:False:Writes the first input to this port if the condition is not met. Else, doesn't write anything.


..
    NEW BLOCK: adder

<a name='adder-ref'></a>

## Add
Adds two floating point numbers together.
If any non-numeric values are passed (like text), then zero is is used in place of that input.

Output:Output:The result of both numbers added together.
Input:Input 1:The first value to operate on
Input:Input 2:The second value to operate on

..
    NEW BLOCK: addminutes

<a name='addminutes-ref'></a>

## AddMinutes
Adds the given number of minutes to a [timestamp](datetimes) and outputs a new [timestamp](datetimes).
The first input specifies a valid [timestamp](datetimes). It can also be a textual representation of a [timestamp](datetimes)
The minutes to add can be negative, allowing you to calculate a [timestamp](datetimes) in the past.

Since [timestamp](datetimes) values are in UTC, no day-light savings are observed.

{% hint type="seealso" %}
    [datetimeformats](datetimeformats) {% endhint %}

Input:Input 1:A valid [timestamp](datetimes)
Input:Input 2:The number of minutes to add
Output:Output:A new [timestamp](datetimes)

..
    NEW BLOCK: adddays

<a name='adddays-ref'></a>

## AddDays
Adds the given number of days to a [timestamp](datetimes) and outputs a new [timestamp](datetimes).
The first input specifies a valid [timestamp](datetimes). It can also be a textual representation of a [timestamp](datetimes)
The days to add can be negative, allowing you to calculate a [timestamp](datetimes) in the past.

Since [timestamp](datetimes) values are in UTC, no day-light savings are observed.

{% hint type="seealso" %}
    [datetimeformats](datetimeformats) {% endhint %}

Input:Input 1:A valid [timestamp](datetimes)
Input:Input 2:The number of days to add
Output:Output:A new [timestamp](datetimes)

..
    NEW BLOCK: addmonths

<a name='addmonths-ref'></a>

## AddMonths
Adds the given number of months to a [timestamp](datetimes) and outputs a new [timestamp](datetimes).
The first input specifies a valid [timestamp](datetimes). It can also be a textual representation of a [timestamp](datetimes)
The months to add can be negative, allowing you to calculate a [timestamp](datetimes) in the past.

Since [timestamp](datetimes) values are in UTC, no day-light savings are observed.

{% hint type="seealso" %}
    [datetimeformats](datetimeformats) {% endhint %}

Input:Input 1:A valid [timestamp](datetimes)
Input:Input 2:The number of months to add
Output:Output:A new [timestamp](datetimes)

..
    NEW BLOCK: addyears

<a name='addyears-ref'></a>

## AddYears
Adds the given number of years to a [timestamp](datetimes) and outputs a new [timestamp](datetimes).
The first input specifies a valid [timestamp](datetimes). It can also be a textual representation of a [timestamp](datetimes)
The years to add can be negative, allowing you to calculate a [timestamp](datetimes) in the past.

Since [timestamp](datetimes) values are in UTC, no day-light savings are observed.

{% hint type="seealso" %}
    [datetimeformats](datetimeformats) {% endhint %}

Input:Input 1:A valid [timestamp](datetimes)
Input:Input 2:The number of years to add
Output:Output:A new [timestamp](datetimes)

..
    NEW BLOCK: concat

<a name='concat-ref'></a>

## Combine
Combines two pieces of text together.
Any inputs which are not textual are converted to a textual representation before combining them.

{% hint type="note" %}
    If you need to combine multiple pieces of text together, avoid chaining [concat-ref](concat-ref) blocks.
    Instead, use a [template-ref](template-ref) block. {% endhint %}

Input:Input 1:First piece of text
Input:Input 2:First piece of text
Output:Output:The combined text


..
    NEW BLOCK: subtractor

<a name='subtractor-ref'></a>

## Subtract
Subtract the second floating point number from the first one.
Both inputs are converted into floating point - if any non-numeric inputs are passed, they are treated as 0.

Input:Input 1:The value to subtract from
Input:Input 2:The value to subtract
Output:Output:The result of the subtraction

..
    NEW BLOCK: multiplier

<a name='multiplier-ref'></a>

## Multiply

Input:Input 1:The first value to operate on
Input:Input 2:The second value to operate on

..
    NEW BLOCK: divider

<a name='divider-ref'></a>

## Divider

Input:Input 1:The first value to operate on
Input:Input 2:The second value to operate on

..
    NEW BLOCK: minute

<a name='minute-ref'></a>

## Minute
Extracts the minutes component of a date/time field.

Output:Output:The minutes component of the date/time (0-59)
Input:Input:A valid datetime object or the datetime as text specified in a [valid format](datetimeformats)

..
    NEW BLOCK: hour

<a name='hour-ref'></a>

## Hour
Extracts the hours component of a date/time field.

Output:Output:The hours component of the date/time (0-23)
Input:Input:A valid datetime object or the datetime as text specified in a [valid format](datetimeformats)

..
    NEW BLOCK: dayofweek

<a name='dayofweek-ref'></a>

## Day Of Week
Extracts the day of week for the date/time field.

Output:Output: Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday
Input:Input:A valid datetime object or the datetime as text specified in a [valid format](datetimeformats)

..
    NEW BLOCK: dayofmonth

<a name='dayofmonth-ref'></a>

## Day Of Month
Extracts the day component of a date/time field.

Output:Output:The day of the month (0-28/30/31)
Input:Input:A valid datetime object or the datetime as text specified in a [valid format](datetimeformats)

..
    NEW BLOCK: year

<a name='year-ref'></a>

## Year
Extracts the year component of a date/time field.

Output:Output:The year, as a number
Input:Input:A valid datetime object or the datetime as text specified in a [valid format](datetimeformats)

..
    NEW BLOCK: datetime

<a name='datetime-ref'></a>

## DateTime
Construct a new [timestamp](datetimes) from an year/month/day/hour/minute/second

Input:Year:
Input:Month:
Input:Day:
Input:Hour:
Input:Minute:
Input:Second:

Output:Output:A [timestamp](datetimes) constructed from the given inputs

..
    NEW BLOCK: actionoutput

<a name='actionoutput-ref'></a>

## Output
Used to return a value from a action sequence.
The output is always a JSON structure and the mime type used is `application/json`.
Values are returned as key/value pairs by default.
Multiple key/value pairs can be returned by using multiple [actionoutput-ref](actionoutput-ref) blocks.

If you wish to return a raw structure and not just key/value pairs,
then use a single [actionoutput-ref](actionoutput-ref) block and pass the json structure in text form as the value
and leave the Field name empty.

### Inputs
Input:Value:The value to return

Field:Field:The key name to use

..
    NEW BLOCK: scheduleaction

<a name='scheduleaction-ref'></a>

## Schedule Action
Schedule an action to be executed later.
To schedule an action, drag in an [Action Start](actionstart-ref) block and build your flow in that block.
Then link the *Action* pin from the schedule block to the blue pin of the [Action Start](actionstart-ref) block.
Then, when the schedule block fires, it will setup a scheduler to execute that action at some later point.

The action is executed exactly once and the schedule is removed once the action is executed.

Input:Time:The [timestamp](datetimes) at which the action should be executed
Input:Action:The action to execute.

..
    NEW BLOCK: repeataction

<a name='repeataction-ref'></a>

## Repeat Action
The Repeat Action block is used to loop through a list of data and execute an action for each item in the list.

### Specifying Inputs
The input list can be a [result set](dt-results), a list of strings (ex, output of a [splittext-ref](splittext-ref) block) or any javascript array (the output from a |javascript| block).

### Specifying the looping logic
The way a repeat block works, is that it executes an [Action Start](actionstart-ref) block for each item in the input list.
To specify what action should execute, drop in an [Action Start](actionstart-ref) block and then link the *Action* output pin of the Repeat block to the blue pin on the [Action Start](actionstart-ref) block.
This action will be executed for each item in the loop.
Since the logic is executed in a different action, you cannot link blocks from your current sequence (where your repeat block is) to items in the loop action.

#### Passing items to the action
Each time the action block is called, a single item from the list is passed as input to the action, along with any data specified in the *Extra* input.
If the item being passed to the action block is a [dictionary](dictionaries) or [result set](dt-results), then it will be split into key/value pairs and sent to the action.
This means, you can add output pins in the [Action Start](actionstart-ref) block to auto extract the fields of the [dictionary](dictionaries).
The *Extra* parameter is passed as an extra key/value pair with the key name being code/Extra.

{% hint style="info" %}

    If your dictionary happens to have a key called code/Extra it will get overwritten by the *Extra* parameter passed into the repeat block.

{% endhint %}


If the item being passed into the action block is *not* a [dictionary](dictionaries) or [result set](dt-results) then the item is passed as a single key/value pair with a key  code/Item.
The *Extra* parameter is passed as a second key/value pair with the key name being code/Extra.
In this case, you can add two output pins to the action block to extract the values:

    1. code/Item
    2. code/Extra


### Order of execution
Lucy makes no guarantees about the order of execution of items in the list.
They are sent to the actions in order, but Lucy may choose to optimize the sequence by running multiple items in parallel.

### Error Handling
Any error that occurs during the execution of the loop action does not affect subsequent items in the list.
Each will get executed independent of errors to any previous executions.

Input:Action:The action block to execute for each item in the list
Input:Items:The list of items to execute. This can be a [result set](dt-results) or a list or array
Input:Extra:Any extra data to be passed along to the action that is called for each item in the list. Use this to send some extra fixed set of information to each item.
Output:Done:The number of items processed is written to this output once all inputs have been processed. Anthing attached to this pin will execute after the full loop is done.


..
    NEW BLOCK: splittext

<a name='splittext-ref'></a>

## Split Text
Create a list from a comma separated list of items.

Actually, create a list by splitting text by any delimiter.

Input:Text:The text to split
Input:Delimiter:The delimiter to use. Can be a character or some text. Typically, code/, is used
Output:Items:A list of split items.

..
    NEW BLOCK: actionstart

<a name='actionstart-ref'></a>

## Action
Used to define a new action in a model

{% hint style="seealso" %}

    Actions are covered in depth in
    [actions](actions)

{% endhint %}

..
    NEW BLOCK: eventstart

<a name='eventstart-ref'></a>

## Event Trigger
Used to listen for and react to events that are sent into the system.

{% hint style="seealso" %}

    Events are covered in depth in
    [eventhandling](eventhandling)

{% endhint %}

..
    NEW BLOCK: callaction

<a name='callaction-ref'></a>

## CallAction
Call an action in a model.
Use this to run a action sequence from within the current action sequence.
Execution is halted until execution finishes and the result is then made available.
If an error ocurred during execution of the action, then the current action sequence is aborted
with an error.


Any parameters to be passed to the action can also be passed as inputs. Click the *Add Input Parameter* link in the Properties Panel to add additional inputs.
You can quickly add multiple inputs at once by specifying them as a comma separated list.

{% hint style="info" %}

    When calling an action in this way, you can only specify parameters to the action in key/value format.
    Unstructured JSON cannot be used.

{% endhint %}

If the action returns a [Dictionary](dictionary) then you can auto-extract values by adding new output pins.
Click the 'Add Output Parameter' link in the Properties Panel to add outputs.

Field:Model:The name of the model in which the action to be called is defined in
Field:Action:The name of the action to call
Input:Instance:the key for the model instance to call the action in. If left off, the action will be called on the model.
Output:All Output:Contains the output from calling the action

..
    NEW BLOCK: fireevent

<a name='fireevent-ref'></a>

## Fire Event
Use this block to trigger a new event.
The event being triggered does not have to be registered in the system.
Any ad-hoc event id can be used.
Any input parameters you specify get sent as part of the event payload.

Field: EventID: The id of the event to trigger

Input:*Multiple*:Add new inputs by clicking the 'Add Input Parameter' link in the properties panel.

..
    NEW BLOCK: callservice

<a name='callservice-ref'></a>

## Call Service
Call a service in an iviva app.

All service return a [result set](dt-results). You can auto-extract values by adding new output pins.
Services are of two forms:

```

    <app>.<model>:<service>

```

or

```

    <app>.<service>

```

{% hint style="warning" %}

    Make sure the service you are calling is supported. Many services may be internal and subject to change.

{% endhint %}

Click the 'Add Output Parameter' link in the Properties Panel to add outputs.

Field:Service:The service to be called
Output:All Output:Contains the [result set](dt-results) from calling the service

..
    NEW BLOCK: calldatasource

<a name='calldatasource-ref'></a>

## Call Data Source
Query a [data source](datasources) in a linked [UI Bundle](uibundles) and return the result of it.
The data source must be defined in a UI bundle that is linked to the specified model.

If an error ocurred during execution of the action, then the current action sequence is aborted
with an error.

All data sources return a [result set](dt-results).

Field:Model:The name of the model in which the action to be called is defined in
Field:Data Source:The name of the data source to query. The data source is defined in the UI Bundle linked to the specified model.

### Inputs
Input:*Multiple*: Any parameters to be passed to the action can also be passed as inputs. Click the *Add Input Parameter* link in the Properties Panel to add additional inputs. You can quickly add multiple inputs at once by specifying them as a comma separated list.


Output:*All Output*:Contains the output from calling the action. This will be a [result set](dt-results). This will often contain multiple ditionaries. You can treat it as a single dictionary in which case, retrieving values will return from the first item. You can also feed the output to any list processing block like a [repeataction-ref](repeataction-ref) block.
Output:*Multiple*: You can can auto-extract values from the first result by adding new output pins. Click the 'Add Output Parameter' link in the Properties Panel to add outputs.

{% hint style="seealso" %}

    [datasources](datasources)

{% endhint %}


..
    NEW BLOCK: activate

<a name='activate-ref'></a>

## Activate
Marks the current model instance as active.

Output:Output:The key of the model instance

..
    NEW BLOCK: addweblet

<a name='addweblet-ref'></a>

## AddWeblet
Add a weblet to the dynamic dashboard of a model.
Select any weblet from the system to be shown. When you choose a weblet, the input pins
of the block will change to reflect the inputs that are required from the weblet.

{% hint style="info" %}

    The colors and placement of the weblet are chosen dynamically by Lucy based on the current dashboard configuration.

{% endhint %}

### Inputs
Input:Params:The parameters to pass to the weblet. This can either be a json object as text or a dictionary.

.. seealso:

    [dictionaries](dictionaries)


..
    NEW BLOCK: constructor

<a name='constructor-ref'></a>

## Initialize
This is a starting block used to trigger a action sequence whenever a new model instance is created.
Use this to run any initialization sequences that have to be executed when a new model instance is created from a model.
You can have multiple of these blocks and they will all execute.

..
    NEW BLOCK: currentitem

<a name='currentitem-ref'></a>

## CurrentItem
Returns the key of the current model instance the action sequence is running.
If the action sequence is running on a model then 0 is returned.

Output:Output:The key of the current model instance. 0 if the current action sequence is running in a model.

..
    NEW BLOCK: currentuser

<a name='currentuser-ref'></a>

## CurrentUser
Returns information about the user the current action sequence is being executed by.

If the action sequence is executed through an API call, then the user associated with the API Key is used.
If the action sequence is run by some automated job in the backend, then no user is present and all outputs will be empty.

### Outputs
- **UserKey**: The key of the logged-in user
- **FullName**: The full name of the user
- **Phone**: The user's phone number
- **Email**: The user's email address
- **LoginID**: The iviva login id for the user
- **UserType**: The user type that the user is tagged with in iviva
- **SiteKey**: The key of the site that the user belongs to

..
    NEW BLOCK: deactivate

<a name='deactivate-ref'></a>

## Deactivate
Deactivae the current model instance.
This block has no effect when being called from a model.

..
    NEW BLOCK: debug

<a name='debug-ref'></a>

## Debug
Use the Debug block to log data to the debug console.

{% hint style="seealso" %}

    [debugging](debugging)

{% endhint %}

Input:Input:The object to be dumped to the debug log. This is serialized to JSON when logged.
Input:Message:Any additional message to be recorded along with the object
Output:Output:The objectt that was sent as input is passed through as output

..
    NEW BLOCK: exception

<a name='exception-ref'></a>

## Exception
Generate an error and halt execution of the action sequence.
An error will be thrown with the specified error message and no further execution of that action sequence will occur.
This is useful to signal error conditions in the action sequence as well as for input validation for action sequences that are meant to be called from a UI.

Input:Message:The error message to be used when the error is generated


..
    NEW BLOCK: exists

<a name='exists-ref'></a>

## Exists
Checks if the input value is valid.
Writes to the `True` output if the value is valid.
If the value is invalid, the `False` output is written to.
Only one of them will be executed.

   	The following values are deemed **invalid**:

   	 - **empty**
   	 - 0
   	 - code/false

   	 All other values are deemed to be **valid**

Input:Input 1:The value to check for existence
Output:True:The input value is written to this output if the input is valid
Output:False:The input value is written to this output if the input is invalid

..
    NEW BLOCK: extractvalue

<a name='extractvalue-ref'></a>

## ExtractValue
Extracts a value from a [dictionary](dictionaries).
Specify an input dictionary and a field, and the value  for that field from the dictionary will be written to the output.
If the dictionary does not contain the given field, empty text will be written to the output.

Input:Input: The input dictionary
Output:Output: The value of the specified key in the dictionary
Field:Field: The name of the field, for which a value should be extracted.

..
    NEW BLOCK: attributeget

<a name='attributeget-ref'></a>

## Get Attribute
Gets the value of an attribute in an model instance.
You can create this block from the Attribute Editor by going to an attribute and dragging the getter icon into the design area.

This block returns the value of the attribute when the block is first called.
If the block's value is read multiple times (ie, there are multiple connections from the output pin),
then the same value is returned each time it is called.

{% hint type="note" %}
    If you expect the value of an attribute to change after it is first read, drag in a second block to read it again later. {% endhint %}

Output:Output:The value of the attribute when the block is executed.

..
    NEW BLOCK: mergedata

<a name='mergedata-ref'></a>

## Merge Data
Merge a name/value pair into a [dictionary](dictionaries).
Use this to add a name/value pair to an existing dictionary.
Or, to create a new dictionary with a given name/value pair.
If the `Input` dictionary is empty, then a new dictionary is created and the name/value pair are added to it.
If the `Input` dictionary exists, then, it is merged with the new name/value pair and the new dictionary is returned in the output.
If the `Input` contains a value but is not a dictionary, a default new dictionary is created with one name/value pair with
a name *value* and the value being the input value.

{% hint style="info" %}

    If the name being merged already exists in the dictionary, then it will be overwritten with the new value

{% endhint %}

Input:Input:The dictionary to add the new name/value pair into
Input:Name:The name of the field to be added to the dictionary
Input:Value:The value to be added to the dictionary
Output:Output:The new dictionary containing the newly added name and value

..
    NEW BLOCK: fromjson

<a name='fromjson-ref'></a>

## Parse JSON
Parses a json block into a [dictionary](dictionaries) or a [result set](dt-results)
The input json structure must either be an object or an array of homogenous objects.

Input:Input:The json text to be parsed
Output:Output:The resulting [dictionary](dictionaries) or [result set](dt-results)

..
    NEW BLOCK: passvalue

<a name='passvalue-ref'></a>

## InjectValue
Used to inject a value into a block.
This is primarily used for flow-control in blocks that don't support a trigger pin.
The value written to the input pin is written to the output only when the trigger port has a value written to it.
This is useful to ensure that certain parts of a sequene are executed before another.

{% hint type="seealso" %}
    See [dataflow](dataflow) for more information on controlling data flow through a action sequence {% endhint %}

Input:Value: The value to inject when something is written to the trigger port
Output:Output: The value specified in the input. This is written only once the trigger port has a value written to it.

..
    NEW BLOCK: tojson

<a name='tojson-ref'></a>

## Serialize JSON
Serialize the input object into JSON text.
If the input is a [dictionary](dictionaries), it will get serialized as a JSON object:

```

    {"key1":"value1","key2":"value2"}

```

If the input is a [result set](dt-results), it will get serialzed as an array of objects:

##### .. code::
        {"key1":"value1","key2":"value2"},
        {"key1":"value1","key2":"value2"},
######         {"key1":"value1","key2":"value2"}


Any other type of input gets converted to text and stored in a JSON object with a key called 'value'

```

    {"value":"2015-01-01 12:240"}

```

Input:Input:The object to be serialized as JSON.
Output:Output:The serialized JSON.

..
    NEW BLOCK: attributeset

<a name='attributeset-ref'></a>

## Set Attribute
Sets the value of an attribute in an model instance.
You can create this block from the Attribute Editor by going to an attribute and dragging the setter icon into the design area.

This block sets a value to the attribute and then passes that value to the output pin.


Input:Input:The value to set to the attribute
Output:Output:The newly written value is passed to the output pin.

..
    NEW BLOCK: setname

<a name='setname-ref'></a>

## SetName
Sets the name associated with the current model instance.

{% hint style="seealso" %}

    [instanceattrs](instanceattrs)

{% endhint %}

Input:Name:The name to set for the current model instance.
Output:Output:The name is passed through to the output.

..
    NEW BLOCK: template

<a name='template-ref'></a>

## Template
Use a template to generate textual output.

This block lets you define a template and specify variables to it to generate a final textual output.

Use it to compose a long messages suitable for email or sms or other types of notification.
It can also be used easily generate xml blocks with placeholders replaced by input values.

The templating system lets you do simple variable substitution, as well as looping through result sets and transformting values.

### Template Syntax

Any text you enter will get directly passed to the output, unless it is enclosed in either code/${...} or code/#{...} blocks.

####### Variables
Variables can be specified using code/#{varname} syntax.
All inputs to the block are available as variables.  The names of the variables will be the names of the input pins.

Example (assume two input pins have been added - code/name and code/ticketid):
.. code::

    Dear #{name}

    Your ticket has been filed in our system.

    Your ticket id is: #{ticketid}

    thanks

    Support Team

####### Dictionaries and Result Sets
If the input contains a [dictionary](dictionaries) or [result set](dt-results) then you can access fields of the object using code/. syntax.

Example (assuming the block has an input called `input1` which contains a dictionary of user details):

```

        Dear #{input1.FirstName},
        Your blah blah blah will be available shortly

```

        thanks

In the case of a [result set](dt-results), the first field from the first record in the [result set](dt-results) is  used.

####### Lists
If the inputs to the block contain a list of items (a list of strings, or a [result set](dt-results) for example),
you can loop through the list using a code/${for }...${end} block.
Any thing within that block will get repeated for each item in the list.
The code/${for} blocks can also be nested for using loops within loops.

The syntax for the loop is:

```

#     ${for loop-variable in list}
    ${end}

```

Within the `for` block, you can use code/#{loop-variable} to access each item.
You can also use code/#{index} to access the iteration count (starts with zero)

Example (given a list of strings, say by using the [splittext-ref](splittext-ref) block):

```

        Here are your tasks:
        ${for x in items}
            * #{x}
        ${end}

```

If the list is a [result set](dt-results) then individual fields of the result could be accessed using the code/. operator.

Example (given an input coming from a datasource)

```

        Here are your tasks:
        ${for row in tasks}
            #${row.TaskName} - Due on: #{row.Deadline}
        ${end}

```


####### Functions
The templating system has many functions that can be used to transform variables or generate values.
Functions use the following syntax:

```

    functionname()
    functionname(arg1,arg2,arg3,...)

```

Each argument could be a variable, a string literal, a number or the result of another function call.

String literals are enclosed in square brackets: `[this is a string literal]`

Example:

```

    functionname(arg1func(),12,[third argument])

```


Available Functions:

.. list-table::
    :header-rows: 1

    * - Function Name
      - Description

    * - html(content)
      - Escape the html inside `content`. This converts '<' into &amp; and so on

    * - date(text)
      - Parses a textual representation of a date/time into a [timestamp](datetimes)

    * - dateonly(date)
      - Removes the time component of a [timestamp](datetimes) - ie, sets the time to 12:00AM

    * - addmonths(date,months)
      - Add `months` to the [timestamp](datetimes) `date` and return the new [timestamp](datetimes)

    * - adddays(date,months)
      - Add `days` to the [timestamp](datetimes) `date` and return the new [timestamp](datetimes)

    * - addyears(date,months)
      - Add `years` to the [timestamp](datetimes) `date` and return the new [timestamp](datetimes)

    * - addminutes(date,months)
      - Add `minutes` to the [timestamp](datetimes) `date` and return the new [timestamp](datetimes)

    * - addhours(date,months)
      - Add `hours` to the [timestamp](datetimes) `date` and return the new [timestamp](datetimes)

    * - select(list,field-to-select,field-to-filter,value-to-filter)
      - Given a list of items `list`, return the field `field-to-select` of the first result where the value of the field `field-to-filter` matches `value-to-filter`. Example: code/select(items,[Name],[UserKey],12) - selects the `FirstName` field of the user having code/UserKey=12

    * - selectfromindex(list,index,field)
      - Given a list of items `list`, return the field `field` from the item in the list with zero-based index `index`. Example: code/selectfromidnex(items,3,[Name]) - Selects the name field from the 4th item in the list

    * - concat(item1,item2,item3,...)
      - Performs string concatenation on a list of items
    * - sum(item1,item2...)
      - Adds all the items together. Items are converted to integers before being added together.
    * - mod(item1,item2)
      - Performs a modulus operation: code/item1 % item2. Both items are converted to integers first.
    * - div(item1,item2)
      - Divides item1 by item2. Both items are converted to integers first.
    * - mul(item1,item2,....)
      - Performs integer multiplication on all items.
    * - fmul(item1,item2,...)
      - Performs floating point multiplication on all items
    * - random(start,end)
      - Returns a random integer between `start` and `end`
    * - randomchoice(item1,item2...)
      - Picks one of the specified items at random
    * - startswith(haystack,needle)
      - Returns true if the text `haystack` begins with the text `needle`. This is case-insensitive.
    * - substring(text,index,[length])
      - Returns a substring of `text` starting at `index`. If `length` is specified, then a maximum of that many characters is returned. Otherwise, the full text from the `index` up to the end of the text is returned.
    * - escapexml(text)
      - Escapes the text so that its suitable for including within an xml block. Example: code/escapexml([Ben & Jerrys]) translates to code/Bend &amp; Jerrys
    * - datetimeformat(timestamp ,[timezone])
      - Given a [timestamp](datetimes), converts it into a nicely formatted string according to the date and time formats given in iviva account settings. Optionally specify a [timezonecodes](timezonecodes) to convert the timestamp into before formatting
    * - dateformat(timestamp)
      - Given a [timestamp](datetimes), converts it into a nicely formatted date string according to the date format given in iviva account settings.


Input:*Multiple*:The inputs to be accessed as variables. You can define as many as you need.
Output:Output:The final text output after rendering the template using the inputs
Field:Template:The actual template to use.

..
    NEW BLOCK: javascript

<a name='javascript-ref'></a>

## Javascript
Executes custom javascript you write. This block has access to its inputs by reading data from inputs.inputName;
You can write outputs by writing data to output.OutputName.
If no data is written to an output port, that port's connections are not followed.
So you can use  a javascript block to handle control-flow by choosing which outputs to write to, based on the inputs.
For reference on what functions are available in javascript, see the Javascript Library section.

{% hint style="seealso" %}

    [javascriptlib](javascriptlib)

{% endhint %}

Input:*Multiple*:Any inputs you add can be accessed via code/inputs.inputName
Output:*Multiple*:Any outputs you add can be written to via :code:'outputs.outputName'
Field:Name:A label for the javascript block to show in the designer
Field:Code:The actual javascript code

..
    NEW BLOCK: parsedate

<a name='parsedate-ref'></a>

## Parse Date
This block converts a textual representation of a [timestamp](datetimes) into an actual [timestamp](datetimes).
See [datetimeformats](datetimeformats) for more information on the formats in which the input can be specified.
If the input is not in any of those formats, Lucy tries to make a guess as to how it should be intrepreted.
Don't like the sound of that? Then specify the date in a valid format :)

Input:Input String:The string to convert into a [timestamp](datetimes)
Output:Output Date:The [timestamp](datetimes)

..
    NEW BLOCK: regexcapture

<a name='regexcapture-ref'></a>

## RegexCapture
Specify a regular expression with capture groups and extract all matches from a given input text.
For each capture group you specify, add an output pin with a name matching the name of the capture group.
All input text that matches each capture group will be written to the corresponding output pin.

.. seealso:

    See https://msdn.microsoft.com/en-us/library/az24scfc(v=vs.110).aspx for information on the regular expression syntax to use.

    See https://msdn.microsoft.com/en-us/library/bs2twtah(v=vs.110).aspx for more information on capture groups.

Input:String:The string to match against
Input:Pattern:The regular expression pattern to use
Output:*Multiple*:Add an output for each capture group in your regular expression. A list of matched strings for that capture group will be written to the output.

..
    NEW BLOCK: actionbinaryoutput

<a name='actionbinaryoutput-ref'></a>

## Binary Output
This block is used to make a action sequence return binary data.
If no content type is supplied, a default of `application/octet-stream` is used.
When called via a web service call, if a file name is specified, then an additional
Content-Disposition header is sent:

```

    Content-Disposition:attachment; filename=<filename>

```

Input:Data:A [binary data object](binobjects) object or text
Input:Content Type:The mime type of the content being returned
Input:File Name:An optional file name to use when the data is downloaded.

..
    NEW BLOCK: objectaction_System_Now

<a name='objectaction_System_Now-ref'></a>

## Now

          Returns the current [timestamp](datetimes) in UTC format.

          Output:Output:The current [timestamp](datetimes)


..
    NEW BLOCK: objectaction_System_GetAccountSetting

<a name='objectaction_System_GetAccountSetting-ref'></a>

## GetAccountSetting

          Reads a global setting in the current iviva account.
          Account settings are stored as key/value pairs, with values being text-based.

          Input:Key:The setting to read
          Output:Output:The setting value. An empty string is returned if the setting is not present.


..
    NEW BLOCK: objectaction_System_SetAccountSetting

<a name='objectaction_System_SetAccountSetting-ref'></a>

## SetAccountSetting

          Writes a global setting in the current iviva account.
          Account settings are stored as key/value pairs, with values being text-based.

          Input:Key:The name to write
          Input:Value:The value to write
          Output:Output:The value that was written


..
    NEW BLOCK: objectaction_System_GetUserByID

<a name='objectaction_System_GetUserByID-ref'></a>

## GetUserByID

          Retrieve the iviva user key for the user having the specified login id.
          Returns nothing if a user with the specified login id does not exist.

          Input:LoginID:The login id of the iviva user
          Output:Output:The user key of the user having the specified login id


..
    NEW BLOCK: objectaction_System_PublishMessage

<a name='objectaction_System_PublishMessage-ref'></a>

## PublishMessage

          Publish a message to the message bus.

{% hint style="seealso" %}

              [mbpublish](mbpublish)

{% endhint %}

          Input:Channel: The channel to publish the message on
          Input:Message: The message to publish. This should be text.


..
    NEW BLOCK: objectaction_System_PublishMessageToQueue

<a name='objectaction_System_PublishMessageToQueue-ref'></a>

## PublishMessageToQueue

          Publish a message to the message queue.
          This block returns an integer error code depending on if the message was successfully published or not.

#######           Error Codes

          - 0 - The message was successfully published on the queue and sent over the message bus
          - 2 - The message was not published on the queue successfully
          - 3 - The message was published on the queue but was not sent over the message bus.

{% hint style="seealso" %}

              [mbpublish](mbpublish)

{% endhint %}

          Input:Channel: The channel to publish the message on
          Input:Message: The message to publish. This should be text.
          Input:Lifetime:The lifetime of the message, in seconds. If not set, the message will never expire.

          Output:Output:Error code describing if the message got published or not.


..
    NEW BLOCK: objectaction_System_GenerateID

<a name='objectaction_System_GenerateID-ref'></a>

## GenerateID

          Generate a unique id for an object by using the default ID format settings in iviva.
          The ID format settings are available in iviva under /Apps/System/accountsettings
          Different prefixes may have different ID formats, depending on the application that uses the prefix.
          If you use a custom prefix, the default settings are used.
          You can also choose to pick up the settings for a given ID prefix but override the actual prefix in the ID with one of your own.
          This is useful, for example, if you want to generate IDs for devices using the format:

```

              DVC/<devicetype>/<running number>
              Ex: DVC/AHU/01
                  DVC/FCU/02
                  DVC/PUMP/03

```


          If want the running number to remain the same for all devices regardless of the device type, then use 'DVC' as the prefix, but override the actual generated prefix with 'DVC/<deivcetype>'


          Input:Prefix:The prefix to give for the generated id.
          Input:Override:Use the `prefix` to derive the running number and date format, but override the actual prefix in the id with the one specified. You can leave this empty usually.

          Output:Output:The generated id.