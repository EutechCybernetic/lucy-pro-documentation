
# Blocks

This section documents the standard available blocks in Lucy.


    
[actionbinaryoutput-ref:](actionbinaryoutput-ref:)


## Binary Output

This block is used to make a action sequence return binary data.
If no content type is supplied, a default of `application/octet-stream` is used.
When called via a web service call, if a file name is specified, then an additional
Content-Disposition header is sent:
    
.. code::
    
    Content-Disposition:attachment; filename=<filename>

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Data
      - A [binary data object](binobjects) object or text
    * - Content Type
      - The mime type of the content being returned
    * - File Name
      - An optional file name to use when the data is downloaded.

        
[actionjsonoutput-ref:](actionjsonoutput-ref:)


## JSON Output

This block is used to make a action sequence return json data.

    
.. code::
    
    Content-Disposition:attachment; filename=<filename>

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Data
      - A [JSON](dt-json) object or text

        
[actionoutput-ref:](actionoutput-ref:)


## Output

Used to return a value from a action sequence.
The output is always a JSON structure and the mime type used is `application/json`.
Values are returned as key/value pairs by default.
Multiple key/value pairs can be returned by using multiple [actionoutput-ref](actionoutput-ref) blocks.
    
If you wish to return a raw structure and not just key/value pairs,
then use a single [actionoutput-ref](actionoutput-ref) block and pass the json structure in text form as the value
and leave the Field name empty.
    
### Inputs


### Fields
.. list-table::
    :header-rows: 1

    * - Field Name
      - Description
    * - Field
      - The key name to use

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Value
      - The value to return

        
[actionstart-ref:](actionstart-ref:)


## Action


    Used to define a new action in a model.
    This block represents the action as a whole and properties for the entire action sequence are set from the [property panel](propertiespanel) for this block.
    You cannot add or delete this block from the [block panel](blockpanel) as this block is mandatory for an action to exist.
    When you add a new action, this block gets created automatically.
    You can add and remove parameters for the action from the [property panel](propertiespanel).
    You can also rename the action from the [property panel](propertiespanel) by using the `Change Name` link.
    When you delete this block, the entire action sequence will be deleted.
    You can also delete the entire action sequence by going to the [action switcher](actionswitcher) and using the image:: images/trash.png icon for the corresponding action sequence.

{% hint type="seealso" %}
      Actions are covered in depth in [actions](actions) {% endhint %}

    

        
[activate-ref:](activate-ref:)


## Activate

Marks the current model instance as active.


### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      - The key of the model instance


        
[adddays-ref:](adddays-ref:)


## AddDays

Adds the given number of days to a [timestamp](datetimes) and outputs a new [timestamp](datetimes).
The first input specifies a valid [timestamp](datetimes). It can also be a textual representation of a [timestamp](datetimes)
The days to add can be negative, allowing you to calculate a [timestamp](datetimes) in the past.
    
Since [timestamp](datetimes) values are in UTC, no day-light savings are observed.
    
    
.. seealso::
    [datetimeformats](datetimeformats)

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Input 1
      - A valid [timestamp](datetimes)
    * - Input 2
      - The number of days to add

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      - A new [timestamp](datetimes)


        
[adder-ref:](adder-ref:)


## Add

Adds two floating point numbers together.
If any non-numeric values are passed (like text), then zero is is used in place of that input.

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Input 1
      - The first value to operate on
    * - Input 2
      - The second value to operate on

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      - The result of both numbers added together.


        
[addminutes-ref:](addminutes-ref:)


## AddMinutes

Adds the given number of minutes to a [timestamp](datetimes) and outputs a new [timestamp](datetimes).
The first input specifies a valid [timestamp](datetimes). It can also be a textual representation of a [timestamp](datetimes)
The minutes to add can be negative, allowing you to calculate a [timestamp](datetimes) in the past.
    
Since [timestamp](datetimes) values are in UTC, no day-light savings are observed.
    
    
.. seealso::
    [datetimeformats](datetimeformats)

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Input 1
      - A valid [timestamp](datetimes)
    * - Input 2
      - The number of minutes to add

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      - A new [timestamp](datetimes)


        
[addmonths-ref:](addmonths-ref:)


## AddMonths

Adds the given number of months to a [timestamp](datetimes) and outputs a new [timestamp](datetimes).
The first input specifies a valid [timestamp](datetimes). It can also be a textual representation of a [timestamp](datetimes)
The months to add can be negative, allowing you to calculate a [timestamp](datetimes) in the past.
    
Since [timestamp](datetimes) values are in UTC, no day-light savings are observed.
    
    
.. seealso::
    [datetimeformats](datetimeformats)

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Input 1
      - A valid [timestamp](datetimes)
    * - Input 2
      - The number of months to add

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      - A new [timestamp](datetimes)


        
[addweblet-ref:](addweblet-ref:)


## AddWeblet

Add a weblet to the dynamic dashboard of a model.
Select any weblet from the system to be shown. When you choose a weblet, the input pins
of the block will change to reflect the inputs that are required from the weblet.
    
.. note::
    
    The colors and placement of the weblet are chosen dynamically by Lucy based on the current dashboard configuration.
    
    
### Inputs

ColorScheme:Number:The color scheme to use for the weblet. Leave this empty to let Lucy dynamically choose the best color scheme based on the current
dashboard configuration. This should be a number from 1-12. 
    
.. seealso: 
    
    [dictionaries](dictionaries)
    


### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Params
      - The parameters to pass to the weblet. This can either be a json object as text or a dictionary.

        
[addyears-ref:](addyears-ref:)


## AddYears

Adds the given number of years to a [timestamp](datetimes) and outputs a new [timestamp](datetimes).
The first input specifies a valid [timestamp](datetimes). It can also be a textual representation of a [timestamp](datetimes)
The years to add can be negative, allowing you to calculate a [timestamp](datetimes) in the past.
    
Since [timestamp](datetimes) values are in UTC, no day-light savings are observed.
    
    
.. seealso::
    [datetimeformats](datetimeformats)

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Input 1
      - A valid [timestamp](datetimes)
    * - Input 2
      - The number of years to add

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      - A new [timestamp](datetimes)


        
[attributeget-ref:](attributeget-ref:)


## Get Attribute

Gets the value of an attribute in an model instance.
You can create this block from the Attribute Editor by going to an attribute and dragging the getter icon into the design area.
    
This block returns the value of the attribute when the block is first called.
If the block's value is read multiple times (ie, there are multiple connections from the output pin),
then the same value is returned each time it is called.
    
.. note::
    If you expect the value of an attribute to change after it is first read, drag in a second block to read it again later.


### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      - The value of the attribute when the block is executed.


        
[attributeset-ref:](attributeset-ref:)


## Set Attribute

Sets the value of an attribute in an model instance.
You can create this block from the Attribute Editor by going to an attribute and dragging the getter icon into the design area.
    
This block returns the value of the attribute when the block is first called.
If the block's value is read multiple times (ie, there are multiple connections from the output pin),
then the same value is returned each time it is called.
    
.. note::
    If you expect the value of an attribute to change after it is first read, drag in a second block to read it again later.


### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      - The value of the attribute when the block is executed.


        
[callaction-ref:](callaction-ref:)


## CallAction

Call an action in a model.
Use this to run a action sequence from within the current action sequence.
Execution is halted until execution finishes and the result is then made available.
If an error ocurred during execution of the action, then the current action sequence is aborted 
with an error.
    
    
Any parameters to be passed to the action can also be passed as inputs. Click the *Add Input Parameter* link in the Properties Panel to add additional inputs.
You can quickly add multiple inputs at once by specifying them as a comma separated list.
    
.. note::
    
    When calling an action in this way, you can only specify parameters to the action in key/value format.
    Unstructured JSON cannot be used.
    
    
    
If the action returns a [Dictionary](dictionary) then you can auto-extract values by adding new output pins.
Click the 'Add Output Parameter' link in the Properties Panel to add outputs.

### Fields
.. list-table::
    :header-rows: 1

    * - Field Name
      - Description
    * - Model
      - The name of the model in which the action to be called is defined in
    * - Action
      - The name of the action to call

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Instance
      - the key for the model instance to call the action in. If left off, the action will be called on the model.

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - All Output
      - Contains the output from calling the action


        
[calldatasource-ref:](calldatasource-ref:)


## Call Data Source

Query a [data source](datasources) in a linked [UI Bundle](uibundles) and return the result of it.
The data source must be defined in a UI bundle that is linked to the specified model.
    
If an error ocurred during execution of the action, then the current action sequence is aborted 
with an error.
    
All data sources return a [result set](dt-results).


### Inputs

{% hint style="seealso" %}

    [datasources](datasources)
    

{% endhint %}

### Fields
.. list-table::
    :header-rows: 1

    * - Field Name
      - Description
    * - Model
      - The name of the model in which the action to be called is defined in
    * - Data Source
      - The name of the data source to query. The data source is defined in the UI Bundle linked to the specified model.

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - *Multiple*
      -  Any parameters to be passed to the action can also be passed as inputs. Click the *Add Input Parameter* link in the Properties Panel to add additional inputs. You can quickly add multiple inputs at once by specifying them as a comma separated list.

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - *All Output*
      - Contains the output from calling the action. This will be a [result set](dt-results). This will often contain multiple ditionaries. You can treat it as a single dictionary in which case, retrieving values will return from the first item. You can also feed the output to any list processing block like a [repeataction-ref](repeataction-ref) block.
    * - *Multiple*
      -  You can can auto-extract values from the first result by adding new output pins. Click the 'Add Output Parameter' link in the Properties Panel to add outputs.


        
[callservice-ref:](callservice-ref:)


## Call Service

Call a service in an iviva app.
    
All service return a [result set](dt-results). You can auto-extract values by adding new output pins.
Services are of two forms:
    
.. code::
    
    <app>.<model>:<service>
    
or
    
.. code::
    
    <app>.<service>
    
.. warning::
    
    Make sure the service you are calling is supported. Many services may be internal and subject to change.
    
Click the 'Add Output Parameter' link in the Properties Panel to add outputs.


### Fields
.. list-table::
    :header-rows: 1

    * - Field Name
      - Description
    * - Service
      - The service to be called


### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - All Output
      - Contains the [result set](dt-results) from calling the service


        
[callwebservice-ref:](callwebservice-ref:)


## Call Web Service

Use this block to call any third party webservice

        
[concat-ref:](concat-ref:)


## Combine

Combines two pieces of text together.
Any inputs which are not textual are converted to a textual representation before combining them.
    
.. note::
    If you need to combine multiple pieces of text together, avoid chaining [concat-ref](concat-ref) blocks.
    Instead, use a [template-ref](template-ref) block.

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Input 1
      - First piece of text
    * - Input 2
      - First piece of text

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      - The combined text


        
[currentitem-ref:](currentitem-ref:)


## CurrentItem

Returns the key of the current model instance the action sequence is running.
If the action sequence is running on a model then 0 is returned.


### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      - The key of the current model instance. 0 if the current action sequence is running in a model.


        
[currentuser-ref:](currentuser-ref:)


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

        
[datetime-ref:](datetime-ref:)


## DateTime

Construct a new [timestamp](datetimes) from an year/month/day/hour/minute/second

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
####     * - Year
####     * - Month
####     * - Day
####     * - Hour
####     * - Minute
####     * - Second

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      - A [timestamp](datetimes) constructed from the given inputs


        
[dayofmonth-ref:](dayofmonth-ref:)


## Day Of Month

Extracts the day component of a date/time field.

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Input
      - A valid datetime object or the datetime as text specified in a [valid format](datetimeformats)

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      - The day of the month (0-28/30/31)


        
[dayofweek-ref:](dayofweek-ref:)


## Day Of Week

Extracts the day of week for the date/time field.

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Input
      - A valid datetime object or the datetime as text specified in a [valid format](datetimeformats)

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      -  Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday


        
[deactivate-ref:](deactivate-ref:)


## Deactivate

Deactivae the current model instance.
This block has no effect when being called from a model.

        
[deadband-ref:](deadband-ref:)


## Deadband


    Emits an output only if the input has changed by the given range
    or if the holding time has expired. 
    Useful if you want to only take action if a value changes by a large amount.


### Fields
.. list-table::
    :header-rows: 1

    * - Field Name
      - Description
    * - Range
      - The range within which, the value will be held. This can be a percentage like '5%' meaning, deviations beyond 5% of the current value will cause the output to be set. It can also be a value like '0.01' meaning if the value changes by more than 0.01 the output will be set.

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Input
      - The value to check

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      - The input value gets emmitted if it passes the deadband criteria


        
[debug-ref:](debug-ref:)


## Debug

Use the Debug block to log data to the debug console.
    
.. seealso::

    [debugging](debugging)

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Input
      - The object to be dumped to the debug log. This is serialized to JSON when logged.
    * - Message
      - Any additional message to be recorded along with the object

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      - The objectt that was sent as input is passed through as output


        
[delay-ref:](delay-ref:)


## Delay


    Pauses execution for the specified time.
    The next connected block is executed only once the delay ends.
    Note that any other branches in your action sequence will continue to execute while this block is on hold.

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Time
      - The number of milliseconds to pause

        
[divider-ref:](divider-ref:)


## Divider

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Input 1
      - The first value to operate on
    * - Input 2
      - The second value to operate on

        
[equals-ref:](equals-ref:)


## Equals

Compares if two inputs are equal. When matching, both inputs are converted to text and matched.
Comparisons are case-insensitive.    


### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Input 1
      - The first value to compare
    * - Input 2
      - The value to compare against

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - True
      - Writes the first input to this port if the condition is met. Else, doesn't write anything
    * - False
      - Writes the first input to this port if the condition is not met. Else, doesn't write anything.


        
[es6javascript-ref:](es6javascript-ref:)


## ES6Javascript


    Executes custom javascript code.

    You have access to ES6 Javascript, including the use of async/await and Promises.
    If you have code that is running asynchronously, the block will finish only after your async code is done.

    You should make this explicit by explicitly calling code/runtime.done() when you are finished with execution.

    This block has access to its inputs by using the code/runtime.inputs() function.
    This will return a Javascript object containing all inputs.
    You can terminate the script and write data to the output ports by calling code/runtime.done(outputs)

    Where code/outputs is a dictionary of values to write to the output pins.
    When code/runtime.done() is called, the script terminates.
    
    If no data is written to an output port, that port's connections are not followed.
    So you can use  a javascript block to handle control-flow by choosing which outputs to write to, 
    based on the inputs.
    For reference on what functions are available in javascript, see the Javascript Library section.

{% hint type="seealso" %}
    
        [es6javascriptlib](es6javascriptlib) {% endhint %}

{% hint style="seealso" %}

        For more information on how data type conversions work with Javascript code, see [datatypes](datatypes)

{% endhint %}

### Fields
.. list-table::
    :header-rows: 1

    * - Field Name
      - Description
    * - Name
      - A label for the javascript block to show in the designer
    * - Code
      - The actual javascript code

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - *Multiple*
      - Any inputs you add can be accessed via code/runtime.inputs()

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - *Multiple*
      - Any outputs you add can be written to via code/runtime.done({..})


        
[eventstart-ref:](eventstart-ref:)


## Event Trigger

Used to listen for and react to events that are sent into the system.
    
.. seealso::

    Events are covered in depth in 
    [eventhandling](eventhandling)

        
[exception-ref:](exception-ref:)


## Exception

Generate an error and halt execution of the action sequence.
An error will be thrown with the specified error message and no further execution of that action sequence will occur.
This is useful to signal error conditions in the action sequence as well as for input validation for action sequences that are meant to be called from a UI.

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Message
      - The error message to be used when the error is generated

        
[exists-ref:](exists-ref:)


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


### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Input 1
      - The value to check for existence

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - True
      - The input value is written to this output if the input is valid
    * - False
      - The input value is written to this output if the input is invalid


        
[extractvalue-ref:](extractvalue-ref:)


## ExtractValue

Extracts a value from a [dictionary](dictionaries).
Specify an input dictionary and a field, and the value  for that field from the dictionary will be written to the output.
If the dictionary does not contain the given field, empty text will be written to the output.


### Fields
.. list-table::
    :header-rows: 1

    * - Field Name
      - Description
    * - Field
      -  The name of the field, for which a value should be extracted.

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Input
      -  The input dictionary

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      -  The value of the specified key in the dictionary


        
[fireevent-ref:](fireevent-ref:)


## Fire Event

Use this block to trigger a new event.
The event being triggered does not have to be registered in the system.
Any ad-hoc event id can be used.
Any input parameters you specify get sent as part of the event payload.


### Fields
.. list-table::
    :header-rows: 1

    * - Field Name
      - Description
    * -  EventID
      -  The id of the event to trigger

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - *Multiple*
      - Add new inputs by clicking the 'Add Input Parameter' link in the properties panel.

        
[fromjson-ref:](fromjson-ref:)


## Convert JSON

Parses a json block into a [dictionary](dictionaries) or a [result set](dt-results)
The input json structure must either be an object or an array of homogenous objects.

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Input
      - The json text to be parsed

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      - The resulting [dictionary](dictionaries) or [result set](dt-results)


        
[getfromredis-ref:](getfromredis-ref:)


## Get Value


  Gets an arbitrary value that was written using [setinredis-ref](setinredis-ref).

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Key
      - The key from which the value should be read

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Value
      - The value to be read. Empty if the key doesn't exist or has expired.


        
[gt-ref:](gt-ref:)


## Greater

Checks if the first value is greater than the second value. 
(Inputs are converted to floating point when compared)


### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Input 1
      - The first value to compare
    * - Input 2
      - The value to compare against

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - True
      - Writes the first input to this port if the condition is met. Else, doesn't write anything
    * - False
      - Writes the first input to this port if the condition is not met. Else, doesn't write anything.


        
[gtd-ref:](gtd-ref:)


## After

Checks if the first datetime occurs after the second date time.


### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Input 1
      - The first value to compare
    * - Input 2
      - The value to compare against

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - True
      - Writes the first input to this port if the condition is met. Else, doesn't write anything
    * - False
      - Writes the first input to this port if the condition is not met. Else, doesn't write anything.


        
[hour-ref:](hour-ref:)


## Hour

Extracts the hours component of a date/time field.

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Input
      - A valid datetime object or the datetime as text specified in a [valid format](datetimeformats)

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      - The hours component of the date/time (0-23)


        
[incrementbyvalue-ref:](incrementbyvalue-ref:)


## Increment By Value


  Increments a counter by the specified value.
  The counter can have an optional expiry which will clear it if its updated within the given time.
  Using an expiry is useful to track how many times an event occurs within a given time period.


### Fields
.. list-table::
    :header-rows: 1

    * - Field Name
      - Description
    * - Expiry
      - The expiry time in seconds for the counter. If the counter is not updated within the given time, it will be deleted. This is optional. If no expiry is given, the counter lives forever

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Key
      - The name of the counter. You can give any name. Counters are shared across all models. If a counter with this name doesn't exist, it will be created and the value set to 0.
    * - Value
      - The numeric value to increment the counter by.

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      - The new value of the counter after incrementing.


        
[injectheaders-ref:](injectheaders-ref:)


## Add Headers

Add additional headers to be included in the api response

        
[javascript-ref:](javascript-ref:)


## Javascript

Executes custom javascript you write. This block has access to its inputs by reading data from inputs.inputName;
You can write outputs by writing data to output.OutputName.
If no data is written to an output port, that port's connections are not followed.
So you can use  a javascript block to handle control-flow by choosing which outputs to write to, based on the inputs.
For reference on what functions are available in javascript, see the Javascript Library section.
    
.. seealso::
    
    [javascriptlib](javascriptlib)

### Fields
.. list-table::
    :header-rows: 1

    * - Field Name
      - Description
    * - Name
      - A label for the javascript block to show in the designer
    * - Code
      - The actual javascript code

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - *Multiple*
      - Any inputs you add can be accessed via code/inputs.inputName

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - *Multiple*
      - Any outputs you add can be written to via :code:'outputs.outputName'


        
[jsonarray-ref:](jsonarray-ref:)


## Make JSON Array


    Makes a JSON array from multiple inputs.
    Optionally provide an existing JSON array  and appends the new items to that.

    You can add  multiple input pins and the value from each pin is taken and combined together to make an array.

    The first input pin - **JSON List** is fixed. You can optionally pass an existing JSON array to it and it will combine the items from that array
    with the other iput pins and output a new JSON Array.
    

        
[jsonexception-ref:](jsonexception-ref:)


## Exception with JSON


    Generates an errorr and halts execution.

    The error message will be formatted as a JSON dictionary. You can add multiple pins to represent keys in the JSON dictionary.
    Pin names will be the key names and the values fed to the pin will be the value of that item in the dictionary.

    The values fed to the pins can be:

    1. text
    2. a [dictionary](dictionaries)
    3. a |JSON| value
    4. an [Array](dt-arrays)

    This block is useful for building an API action sequence that will return an error in JSON format.
    You can use the Code pin to specify an HTTP Status Code for the response.
    This block will also add a code/Content-Type header to the response with the value set to code/application/json.
    

        
[jsonobject-ref:](jsonobject-ref:)


## Make JSON Object


    Use this block to create a new JSON object.
    You can add multiple input pins. The names of the pins are keys. The values will be the value of the corresponding item in the object..

    For example, if you add 2 input pins - 'A', 'B' and 'C' and give the corresponding values as '1' , '2' and code/{"D":3},
    then the output JSON object will be code/{"A":"1","B":"2","C":{"D":3}}

    The input can be

    1. text
    2. a [dictionary](dictionaries)
    3. a |JSON| value
    4. an [Array](dt-arrays)


### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      - JSON Object


        
[jsonpath-ref:](jsonpath-ref:)


## Extract JSON Path


    Takes the input [JSON](dt-json) value and extracts a sub-component of it using the path expression given.

{% hint type="seealso" %}
        http://jsonpath.com for more information {% endhint %}


### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - JSON Object
      - The JSON to extract a sub-component from. This can be a text representation of JSON or a [JSON](dt-json) value.
    * - Path
      - The JSON Path expression to use to find the component to extract from it.

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - All
      - Returns all matches as an array
    * - First
      - Returns the first match. Since its common to only have one match or to only want to process one, this is provideed as a convenience so you don't have to extract the first one out of the array


        
[lookup-ref:](lookup-ref:)


## Lookup


    Use this block to find a value corresponding for the input given.

    You can populate a table of key/value pairs. And then, the input is matched against the table
    and if it matches any keys, the corresponding value is sent to the output.

    This is useful to take, say, a department as input and return the email address of the department's supervisor.
    Use the code/Edit Data link in the [property panel](propertiespanel) to bring up the editor where you can edit the key/value pairs.

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Input
      - The key to look up

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      -  The corresponding value to obtain


        
[lt-ref:](lt-ref:)


## Less

Checks if the first value is less than the second value. 
(Inputs are converted to floating point when compared)


### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Input 1
      - The first value to compare
    * - Input 2
      - The value to compare against

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - True
      - Writes the first input to this port if the condition is met. Else, doesn't write anything
    * - False
      - Writes the first input to this port if the condition is not met. Else, doesn't write anything.


        
[ltd-ref:](ltd-ref:)


## Before

Checks if the first datetime occurs prior to the second date time.


### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Input 1
      - The first value to compare
    * - Input 2
      - The value to compare against

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - True
      - Writes the first input to this port if the condition is met. Else, doesn't write anything
    * - False
      - Writes the first input to this port if the condition is not met. Else, doesn't write anything.


        
[mergedata-ref:](mergedata-ref:)


## Merge Data

Merge a name/value pair into a [dictionary](dictionaries).
Use this to add a name/value pair to an existing dictionary.
Or, to create a new dictionary with a given name/value pair.
If the `Input` dictionary is empty, then a new dictionary is created and the name/value pair are added to it.
If the `Input` dictionary exists, then, it is merged with the new name/value pair and the new dictionary is returned in the output.
If the `Input` contains a value but is not a dictionary, a default new dictionary is created with one name/value pair with 
a name *value* and the value being the input value.
    
.. note::
    
    If the name being merged already exists in the dictionary, then it will be overwritten with the new value

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Input
      - The dictionary to add the new name/value pair into
    * - Name
      - The name of the field to be added to the dictionary
    * - Value
      - The value to be added to the dictionary

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      - The new dictionary containing the newly added name and value


        
[minute-ref:](minute-ref:)


## Minute

Extracts the minutes component of a date/time field.

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Input
      - A valid datetime object or the datetime as text specified in a [valid format](datetimeformats)

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      - The minutes component of the date/time (0-59)


        
[mqttpublish-ref:](mqttpublish-ref:)


## MqttPublish


    Publish a message on an Mqtt topic.
    This will be sent to the mqtt broker which is configured in your Lucy dashboard.


### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Topic
      - The topic to send the message to
    * - Message
      - The message to send. This should be text

        
[multiplier-ref:](multiplier-ref:)


## Multiply

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Input 1
      - The first value to operate on
    * - Input 2
      - The second value to operate on

        
[nequals-ref:](nequals-ref:)


## Not Equal

Compares if two inputs are not equal. When matching, both inputs are converted to text and matched.
Comparisons are case-insensitive.    


### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Input 1
      - The first value to compare
    * - Input 2
      - The value to compare against

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - True
      - Writes the first input to this port if the condition is met. Else, doesn't write anything
    * - False
      - Writes the first input to this port if the condition is not met. Else, doesn't write anything.


        
[notinstalledblock-ref:](notinstalledblock-ref:)


## Not Installed

This block represents a block that has not been installed

        
[objectaction:System:GenerateID-ref:](objectaction:System:GenerateID-ref:)


## GenerateID

Generate a unique id for an object by using the default ID format settings in iviva.
          The ID format settings are available in iviva under /Apps/System/accountsettings
          Different prefixes may have different ID formats, depending on the application that uses the prefix. 
          If you use a custom prefix, the default settings are used.
          You can also choose to pick up the settings for a given ID prefix but override the actual prefix in the ID with one of your own. 
          This is useful, for example, if you want to generate IDs for devices using the format:

          .. code::

              DVC/<devicetype>/<running number>
              Ex: DVC/AHU/01
                  DVC/FCU/02
                  DVC/PUMP/03


          If want the running number to remain the same for all devices regardless of the device type, then use 'DVC' as the prefix, but override the actual generated prefix with 'DVC/<deivcetype>'


### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Prefix
      - The prefix to give for the generated id.
    * - Override
      - Use the `prefix` to derive the running number and date format, but override the actual prefix in the id with the one specified. You can leave this empty usually.

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      - The generated id.


        
[objectaction:System:GetAccountSetting-ref:](objectaction:System:GetAccountSetting-ref:)


## GetAccountSetting

Reads a global setting in the current iviva account.
          Account settings are stored as key/value pairs, with values being text-based.


### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Key
      - The setting to read

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      - The setting value. An empty string is returned if the setting is not present.


        
[objectaction:System:GetUserByID-ref:](objectaction:System:GetUserByID-ref:)


## GetUserByID

Retrieve the iviva user key for the user having the specified login id.
          Returns nothing if a user with the specified login id does not exist.


### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - LoginID
      - The login id of the iviva user

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      - The user key of the user having the specified login id


        
[objectaction:System:Now-ref:](objectaction:System:Now-ref:)


## Now

Returns the current [timestamp](datetimes) in UTC format.

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      - The current [timestamp](datetimes)


        
[objectaction:System:PublishMessage-ref:](objectaction:System:PublishMessage-ref:)


## PublishMessage

Publish a message to the message bus.

{% hint style="seealso" %}

              [mbpublish](mbpublish)

{% endhint %}


### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Channel
      -  The channel to publish the message on
    * - Message
      -  The message to publish. This should be text.

        
[objectaction:System:PublishMessageToQueue-ref:](objectaction:System:PublishMessageToQueue-ref:)


## PublishMessageToQueue

Publish a message to the message queue.
          This block returns an integer error code depending on if the message was successfully published or not.

#####           Error Codes

          - 0 - The message was successfully published on the queue and sent over the message bus
          - 2 - The message was not published on the queue successfully
          - 3 - The message was published on the queue but was not sent over the message bus.

{% hint style="seealso" %}

              [mbpublish](mbpublish)

{% endhint %}


### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Channel
      -  The channel to publish the message on
    * - Message
      -  The message to publish. This should be text.
    * - Lifetime
      - The lifetime of the message, in seconds. If not set, the message will never expire.

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      - Error code describing if the message got published or not.


        
[objectaction:System:SetAccountSetting-ref:](objectaction:System:SetAccountSetting-ref:)


## SetAccountSetting

Writes a global setting in the current iviva account.
          Account settings are stored as key/value pairs, with values being text-based.


### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Key
      - The name to write
    * - Value
      - The value to write

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      - The value that was written


        
[parsedate-ref:](parsedate-ref:)


## Parse Date

This block converts a textual representation of a [timestamp](datetimes) into an actual [timestamp](datetimes).
See [datetimeformats](datetimeformats) for more information on the formats in which the input can be specified.
If the input is not in any of those formats, Lucy tries to make a guess as to how it should be intrepreted.
Don't like the sound of that? Then specify the date in a valid format :)

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Input String
      - The string to convert into a [timestamp](datetimes)

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output Date
      - The [timestamp](datetimes)


        
[parsejson-ref:](parsejson-ref:)


## Parse JSON


    This block parses json text into a [JSON](dt-json) object.

    If the input does not contain valid json, this block will raise an error.

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Input
      - The textual representation of JSON

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      -  The corresponding [JSON](dt-json) value.


        
[passvalue-ref:](passvalue-ref:)


## InjectValue

Used to inject a value into a block.
This is primarily used for flow-control in blocks that don't support a trigger pin.
The value written to the input pin is written to the output only when the trigger port has a value written to it.
This is useful to ensure that certain parts of a sequene are executed before another.
    
.. seealso::
    See [dataflow](dataflow) for more information on controlling data flow through a action sequence

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Value
      -  The value to inject when something is written to the trigger port

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      -  The value specified in the input. This is written only once the trigger port has a value written to it.


        
[publishmessage-ref:](publishmessage-ref:)


## PublishMessage


    Publish a message to the message bus.

{% hint style="seealso" %}

        [mbpublish](mbpublish)

{% endhint %}


### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Channel
      -  The channel to publish the message on
    * - Message
      -  The message to publish. This should be text.

        
[regexcapture-ref:](regexcapture-ref:)


## RegexCapture

Specify a regular expression with capture groups and extract all matches from a given input text.
For each capture group you specify, add an output pin with a name matching the name of the capture group.
All input text that matches each capture group will be written to the corresponding output pin.
    
.. seealso:
    
    See https://msdn.microsoft.com/en-us/library/az24scfc(v=vs.110).aspx for information on the regular expression syntax to use.
    
    See https://msdn.microsoft.com/en-us/library/bs2twtah(v=vs.110).aspx for more information on capture groups.

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - String
      - The string to match against
    * - Pattern
      - The regular expression pattern to use

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - *Multiple*
      - Add an output for each capture group in your regular expression. A list of matched strings for that capture group will be written to the output.


        
[repeataction-ref:](repeataction-ref:)


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
    
.. note::
    
    If your dictionary happens to have a key called code/Extra it will get overwritten by the *Extra* parameter passed into the repeat block.
    

If the item being passed into the action block is *not* a [dictionary](dictionaries) or [result set](dt-results) then the item is passed as a single key/value pair with a key  code/Item.
The *Extra* parameter is passed as a second key/value pair with the key name being code/Extra.
In this case, you can add two output pins to the action block to extract the values:
    
    1. code/Item
    2. code/Extra
    
    
### Order of execution
|Lucy| makes no guarantees about the order of execution of items in the list.
They are sent to the actions in order, but Lucy may choose to optimize the sequence by running multiple items in parallel.
    
### Error Handling
Any error that occurs during the execution of the loop action does not affect subsequent items in the list.
Each will get executed independent of errors to any previous executions.

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Action
      - The action block to execute for each item in the list
    * - Items
      - The list of items to execute. This can be a [result set](dt-results) or a list or array
    * - Extra
      - Any extra data to be passed along to the action that is called for each item in the list. Use this to send some extra fixed set of information to each item.

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Done
      - The number of items processed is written to this output once all inputs have been processed. Anthing attached to this pin will execute after the full loop is done.


        
[scheduleaction-ref:](scheduleaction-ref:)


## Schedule Action

Schedule an action to be executed later.
To schedule an action, drag in an [Action Start](actionstart-ref) block and build your flow in that block.
Then link the *Action* pin from the schedule block to the blue pin of the [Action Start](actionstart-ref) block.
Then, when the schedule block fires, it will setup a scheduler to execute that action at some later point.
    
The action is executed exactly once and the schedule is removed once the action is executed.


### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Time
      - The [timestamp](datetimes) at which the action should be executed
    * - Action
      - The action to execute.

        
[setinredis-ref:](setinredis-ref:)


## Set Value


  Associate a value with a key.
  You can specify an optional expiry time in seconds to make the value get deleted if it's not updated within the given time.
  This block is useful for storing arbitrary values.
  Using the expiry is useful for storing real-time values that need to get deleted if they are stale.
  If the value doesn't get updated in the prescribed time, it will be deleted.


### Fields
.. list-table::
    :header-rows: 1

    * - Field Name
      - Description
    * - Expiry
      - The expiry time in seconds for the value. This can be empty to indicate no expiry.

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Key
      - The key to write the value to
    * - Value
      - The value to write

        
[setname-ref:](setname-ref:)


## SetName

Sets the name associated with the current model instance.
    
.. seealso::
    
    [instanceattrs](instanceattrs)

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Name
      - The name to set for the current model instance.

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      - The name is passed through to the output.


        
[splittext-ref:](splittext-ref:)


## Split Text

Create a list from a comma separated list of items.
    
Actually, create a list by splitting text by any delimiter.

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Text
      - The text to split
    * - Delimiter
      - The delimiter to use. Can be a character or some text. Typically, code/, is used

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Items
      - A list of split items.


        
[stringinterpolate-ref:](stringinterpolate-ref:)


## String Interpolation

{% hint type="warning" %}
    This block has been deprecated. Use a |template-ref| block instead. {% endhint %}

        
[subtractor-ref:](subtractor-ref:)


## Subtract

Subtract the second floating point number from the first one.
Both inputs are converted into floating point - if any non-numeric inputs are passed, they are treated as 0.

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Input 1
      - The value to subtract from
    * - Input 2
      - The value to subtract

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      - The result of the subtraction


        
[template-ref:](template-ref:)


## Template

    Use a template to generate textual output.

    This block lets you define a template and specify variables to it to generate a final textual output.

    Use it to compose a long messages suitable for email or sms or other types of notification.
    It can also be used easily generate xml blocks with placeholders replaced by input values.

    The templating system lets you do simple variable substitution, as well as looping through result sets and transformting values.

###     Template Syntax

    Any text you enter will get directly passed to the output, unless it is enclosed in either code/${...} or code/#{...} blocks.

#####     Variables
    Variables can be specified using code/#{varname} syntax. 
    All inputs to the block are available as variables.  The names of the variables will be the names of the input pins.

    Example (assume two input pins have been added - code/name and code/ticketid):
    .. code::

        Dear #{name}

        Your ticket has been filed in our system.

        Your ticket id is: #{ticketid}

        thanks

        Support Team

#####     Dictionaries and Result Sets
    If the input contains a [dictionary](dictionaries) or [result set](dt-results) then you can access fields of the object using code/. syntax.

    Example (assuming the block has an input called `input1` which contains a dictionary of user details):

    .. code::

            Dear #{input1.FirstName},
            Your blah blah blah will be available shortly

            thanks

    In the case of a [result set](dt-results), the first field from the first record in the [result set](dt-results) is  used.

#####     Lists
    If the inputs to the block contain a list of items (a list of strings, or a [result set](dt-results) for example),
    you can loop through the list using a code/${for }...${end} block.
    Any thing within that block will get repeated for each item in the list.
    The code/${for} blocks can also be nested for using loops within loops.

    The syntax for the loop is:

    .. code::

######         ${for loop-variable in list}
        ${end}

    Within the `for` block, you can use code/#{loop-variable} to access each item.
    You can also use code/#{index} to access the iteration count (starts with zero)

    Example (given a list of strings, say by using the [splittext-ref](splittext-ref) block):

    .. code::

            Here are your tasks:
            ${for x in items}
                * #{x}
            ${end}

    If the list is a [result set](dt-results) then individual fields of the result could be accessed using the code/. operator.

    Example (given an input coming from a datasource)

    .. code::

            Here are your tasks:
            ${for row in tasks}
                #${row.TaskName} - Due on: #{row.Deadline}
            ${end}


#####     Functions
    The templating system has many functions that can be used to transform variables or generate values.
    Functions use the following syntax:

    .. code::

        functionname()
        functionname(arg1,arg2,arg3,...)

    Each argument could be a variable, a string literal, a number or the result of another function call.

    String literals are enclosed in square brackets: `[this is a string literal]`

    Example:

    .. code::

        functionname(arg1func(),12,[third argument])


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


### Fields
.. list-table::
    :header-rows: 1

    * - Field Name
      - Description
    * - Template
      - The actual template to use.

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - *Multiple*
      - The inputs to be accessed as variables. You can define as many as you need.

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      - The final text output after rendering the template using the inputs


        
[tojson-ref:](tojson-ref:)


## Serialize JSON

Serialize the input object into JSON text.
If the input is a [dictionary](dictionaries), it will get serialized as a JSON object:
    
.. code::
    
    {"key1":"value1","key2":"value2"}
    
If the input is a [result set](dt-results), it will get serialzed as an array of objects:
    
####### .. code::
        {"key1":"value1","key2":"value2"},
        {"key1":"value1","key2":"value2"},
########         {"key1":"value1","key2":"value2"}
    
    
Any other type of input gets converted to text and stored in a JSON object with a key called 'value'
    
.. code::
    
    {"value":"2015-01-01 12:240"}

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Input
      - The object to be serialized as JSON.

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      - The serialized JSON.


        
[unknownaction-ref:](unknownaction-ref:)


## Unknown Action

This block represents all blocks that could not be loaded. This likely means you imported a model without having all the connectors in place

        
[waitonchannel-ref:](waitonchannel-ref:)


## Wait on Channel


    Waits on a channel for message.


### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Channel
      - Channel to listen for a message
    * - Timeout
      - Time to wait for a message in millisecond

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Error
      - Error that occurred during processing
    * - Message
      - Message received on the channel


        
[year-ref:](year-ref:)


## Year

Extracts the year component of a date/time field.

### Inputs
.. list-table::
    :header-rows: 1

    * - Input Name
      - Description
    * - Input
      - A valid datetime object or the datetime as text specified in a [valid format](datetimeformats)

### Outputs
.. list-table::
    :header-rows: 1

    * - Output Name
      - Description
    * - Output
      - The year, as a number


        