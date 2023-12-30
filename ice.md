


[ice:](ice:)

# iviva Expression Langauge
The iviva expression language is a domain-specific mini-language that lets you express logic and formatting instructions in textual form. It provides flexibility to intersperse expressions with regular text.
This syntax is used in [template-ref](template-ref) blocks as well as in custom user interfaces to bind data and determine logic.


## Syntax
All expressions by default are just text.
Any special logic, variables and formatting instructions  are wrapped in code/#{....} blocks.
Any text outside of those blocks are treated as literal text.

The following is a valid expression:

.. code::

    Good morning, #{auth.Name}!

In this case, the part wrapped in code/#{...} will be evaluated and the result will be replaced back in the text.
The final text output might be:

    Good morning, Ricky Ricardo!

In this case, code/auth is a special object that represents the currently logged-in user and code/Name is a field of that object that reprsents the user's full name.
See the [icevars](icevars) section for a full list of what variables and objects can be used in expressions.

## Logic
You can use boolean logic as part of your expression.
The following operators are supported:

* code/? - This is the *truthy* operator. It converts any expression preceding it into a true/false value.
The following values evaluate to code/false:

    * *empty string*
    * code/0
    * code/null
    * code/false
    * code/"false" (the text 'false')

Other values evaluate to code/true

* code/and - Example: code/#{firstvar? and secondvar?} - Returns true if both firstvar and secondvar are true
* code/or - Example: code/#{firstvar? or secondvar?} - Returns true if any of firstvar and secondvar are true
* code/not - negates the experssion proceding it - Example: code/#{not firstvar?} - Returns false if firstvar is true

You can use
code/(
and
code/)
to group expressions

Example:

.. code::
    #{not (firstvar? and secondvar?)}

Returns true if either of the values are false

If/else syntax is also supported to evaluate expressions:

.. code::

    #{if firstvar? then secondvar else thirdvar }

This evaluates to code/secondvar if code/firstvar is true, else it evalutes to code/thirdvar

## Formatting
If you need to include literal text inside an expression, put it inside square brackets:

.. code::
    #{if authorized? then [Ok] else [Sorry, no access permitted]}

If the code/authorized variable is true then evaluate to the text "Ok" else evaluate to the text "Sorry, no access permitted"

## Transformers
Transformers are special functions that transform an expression in some way.
Put a pipe (code/|) character after an expression and then the name of the transformer to transform that expression.

One such transformer is the [datetimeformat-transformer](datetimeformat-transformer) transformer.
That transforms an expression which evaluated to a [timestamp](datetimes) into a nicely formatted textual representation of the [timestamp](datetimes) according to the logged-in user's format preferences.

.. code::

    #{services.details.CreatedDateTime|datetimeformat}


This returns the CreateDateTime value in a nicely formatted text.

## Functions
There are several predefined functions that can be used within expressions.
The syntax for functions is:

.. code::
    #{function(arg1,arg2,arg3)}

Functions can be nested.

[icevars:](icevars:)

## Available Variables and Objects

### param
Use this object to read page input values.

Example:
.. code::
    #{if param.enable? then [Ok] else [No]}

Checks if code/enable is passed as a query string parameter and is set to some value except 0 or empty and then returns "OK" or "No" accordingly.

### services
Use this to read data from any datasources defined in a UI bundle.
To read a field from a datasource, the syntax is code/#{sevices.datasource.field}

All the data in a source can be returned as serialized JSON by using:

code/#{services.datasource.__rawdata__|json}

This returns a JSON representation of a data source.
This is useful if you want to process a datasource entirely in javascript on a page.


### authrole
Use this to check if the logged-in user has a specified |approle|

Syntax: code/#{authrole.app.rolename?}

Where code/app is the application name and code/rolename is the name of the role to check

Returns true if the current user has the specified app role.

For checking model roles, use code/#{authrole.Lucy.model.modelname.rolename?}

### baseurl
This variable returns the relative root of the iviva application.
Use this to construct a relative path for a url within iviva

Example:
.. code::
    #{baseurl}/Apps/Lucy/dashboard

### fullaccounturl
The full path to the root of the iviva application.
Use this to construct absolute paths for a url within iviva
Example:
.. code::
    #{baseurl}/Apps/Lucy/dashboard


### auth
Use this object to access details about the logged-in user.
The syntax is code/#{auth.FieldName}

Where code/FieldName can be any  of the following:

* Name - the user's full name
* LoginID - the user's login id
* UserKey - the iviva user key associated with this user.


## Available Transformers
[int-transformer:](int-transformer:)

### int
convert to an integer

[str-transformer:](str-transformer:)

### str
convert to a string

[exists-transformer:](exists-transformer:)

### exists
check if the value is null or empty

[validint-transformer:](validint-transformer:)

### validint
check if the value is a non-zero integer

[float-transformer:](float-transformer:)

### float
convert to a floating point value

[floatstr-transformer:](floatstr-transformer:)

### floatstr(precision)
converts to a formatted string with given precision (from 1 - 7)
Example:

.. code::
    #{row.Value|floatstr(2)} yields 2.23
    #{row.Value|floatstr(3)} yields 2.230

[clip-transformer:](clip-transformer:)

### clip(length)
clip to a specified length and add ellipsis at the end

.. code::
    #{row.Description|clip(25)} - clips the text to have a max of 25 chars and shows ‘…’ at the end

[trim-transformer:](trim-transformer:)

### trim
Trim out the leading and trailing space of strings


[duration-transformer:](duration-transformer:)

### duration
Converts an integer (in minutes) into a user friendly duration
Example:
.. code::
    #{row.TotalMinutes|duration} - returns ‘10min’ or ‘1hr 30min’ or ‘2 days’ etc...

[capitalize-transformer:](capitalize-transformer:)

### capitalize
Capitalizes the first character of the specified text

[dateformat-transformer:](dateformat-transformer:)

### dateformat
Convert the date value into text formatted in the user’s preferred date format

[minutesago-transformer:](minutesago-transformer:)

### minutesago
return how many minutes have passed since the datetime value specified

[datetimeformat-transformer:](datetimeformat-transformer:)

### datetimeformat
Converts the datetime into text using the user’s preferred datetime format and in the user’s timezone

[timeformat-transformer:](timeformat-transformer:)

### timeformat
Converts the time into text using the user’s preferred time format


## Available Functions
[concat-function:](concat-function:)

### concat(str1,str2,…)
combines multiple strings together
Example:

.. code::
    #{concat(row.Url,[?key=],row.Key)} - combines row.Url + ‘?key=‘ + row.Key

[sum-function:](sum-function:)

### sum(i1,i2...)
sum of multiple integers


[mod-function:](mod-function:)

### mod(i1,i2)
i1 % i2


[mul-function:](mul-function:)

### mul(i1,i2,…)
 multiply multiple integers

[fmul-function:](fmul-function:)

### fmul(f1,f2,…)
 multiply multiple floating point values


[random-function:](random-function:)

### random(start,end)
 returns a random number between start and end

[randomchoice-function:](randomchoice-function:)

### randomchoice(item1,item2,…)
returns one of the specified items at random
Example:

.. code::
    #{randomchoice([A],[B],[C])} - returns either ‘A’ ‘B’ or ‘C’ at random

[startswith-function:](startswith-function:)

### startswith(a,b)
returns true if b is a prefix of a (case insensitive)

[substring-function:](substring-function:)

### substring(a,i1)
return a substring of ‘a’ starting at i1 (zero-based index)

[substring-function:](substring-function:)

### substring(a,i1,i2)
return a substring of ‘a’ starting at i1 and i2 characters long

 .. _len-function:

### len(a)
length of the string specified in ‘a'