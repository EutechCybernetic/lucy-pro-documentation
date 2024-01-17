

<a name='es6javascriptlib'></a>

# Javascript Library


The following javascript functions are available for use with the |javascript| block.

<a name='es6jsoi'></a>

## lucy

### model(name)
Creates a new [model reference](es6javascript.md#metadataobject) for the model with the given name

#### Returns
[MetadataObject](MetadataObject)

### createInstance(model,instanceName)
Create a new model instance of a model and give it a name.

#### Returns
MetadataObject

### setOutput(key, value)
Sets an output for an action.

{% hint style="seealso" %}

    [Output](block-source.raw.md#actionoutput-ref)

{% endhint %}


### instance(key)
Obtain a reference to an model instance with the given key.

#### Returns
[MetadataObject](MetadataObject)

### currentModel()
Obtain a reference to the current executing model.

#### Returns
[MetadataObject](MetadataObject)

### currentInstance()
Obtain a reference to the current executing model instance.

#### Returns
[MetadataObject](MetadataObject)

### parseDateTime(dt)
Parse a textual representation of a datetime.

{% hint type="seealso" %}
    [Valid Date/Time Formats](datatypes.md#datetimeformats) {% endhint %}


#### Returns
[timestamp](datatypes.md#datetimes)

<a name='genexcel'></a>

### generateExcelSheet(columns, items)
Generate an excel sheet in xlsx format.
Adds column headers and rows of data.



|`columns`|An array of column headers to add to the top.|
|--|--|
|`items`|An array of objects to be populated as rows. Each object should have fields matching the items in the `columns` array
Example:|
 

```

    var columns = ['First Name','Last Name','Age'];
    var data = [
        {'First Name':'Ricky','Last Name':'Ricardo','Age':36},
        {'First Name':'Ethel','Last Name':'Mertz','Age':34},
        {'First Name':'Fred','Last Name':'Mertz','Age':48}
    ];
    var sheet = oi.generateExcelSheet(columns,data);

```


#### Returns
[binary data object](datatypes.md#binobjects) - the excel sheet as a binary data stream

### currentUser()
Get attributes about the current logged-in user.

#### Returns
[dictionary](datatypes.md#dictionaries) - a dictionary of attributes for the user.
Available fields are:

- UserKey - the iviva user key for the user
- LoginID - the user's iviva login id
- Name - the user's name
- Email - the user's email address
- Phone - the user's phone number
- SiteKey - the user's iviva site that he is configured for

### now()
The current time in UTC format

#### Returns
[timestamp](datatypes.md#datetimes)

<a name='jstzfunctions'></a>

### convertFromUtc(dt, tz)
Converts a [timestamp](datatypes.md#datetimes) from utc to a different timezone.



|`dt`|A [timestamp](datatypes.md#datetimes) to convert to a different timezone|
|--|--|
|`tz`|The [code](timezonecodes.md#timezonecodes) of the timezone to convert to|
 

{% hint style="seealso" %}

    [Working with time zones](datatypes.md#timezones)

{% endhint %}

    [Time Zone Codes](timezonecodes.md#timezonecodes)

#### Returns
[timestamp](datatypes.md#datetimes) converted to a different time zone

### convertToUtc(now, tz)
Converts a [timestamp](datatypes.md#datetimes) to utc from a different timezone.



|`dt`|A [timestamp](datatypes.md#datetimes) to convert to UTC|
|--|--|
|`tz`|The [code](timezonecodes.md#timezonecodes) of the timezone the [timestamp](datatypes.md#datetimes) was currently in.|
 

{% hint style="seealso" %}

    [Working with time zones](datatypes.md#timezones)

{% endhint %}

    [Time Zone Codes](timezonecodes.md#timezonecodes)

#### Returns
[timestamp](datatypes.md#datetimes) converted to a different time zone

### dateOnly(now)
Returns the date only with the time stripped out.

#### Returns
[timestamp](datatypes.md#datetimes)

### escapeXml(name)
Escapes the character sequences suitable for embedding in xml.

#### Returns
string

### isInstance()
Returns true if the current action sequence is executing in an model instance (as opposed to a model)

#### Returns
bool

### logItems(items...)
Logs data to the Global Debug Log.
You can pass in multiple objects here and they will be serialized as JSON and written to the log.


### executeService(service)
Execute an iviva service

#### Returns
[result set](datatypes.md#dt-results)

### executeService(service,parameters)
Execute an iviva service, passing the given parameters

#### Returns
[result set](datatypes.md#dt-results)

### guid()
Generate a globally unique identifier.

#### Returns
string

<a name='uploadData'></a>

### uploadData(name, data)
Upload the given data to the iviva storage, using `name` as a base name.  The actual name used to store the data will be unique and randomly generated using `name` as part of it.
This is to gaurantee no collisions with existing files.

The actual name used to store the data is returned.
This name can be accessed via an http url of the form:

    http://<ivivacloudurl>/content/OI/<filename>



|`name`|The base name for the file|
|--|--|
|`data`|[binary data object](datatypes.md#binobjects) representing the data to be uploaded.
#### Returns
string - the actual file name that the data is saved as.|
 

### uploadDataWithExplicitName(name, data)
Same as [uploadData(name, data)](es6javascript.md#uploadData) except the name specified is the exact name used to save the file. No extra unique postfix is added to the name.

{% hint type="warning" %}
    This could potentially cause existing uploads to be overwritten if not used carefully. Do not use this function unless you have a very good reason for maintaining file names. {% endhint %}

#### Returns
string

### parseDataURI(uri)
Parse a data uri (specified as a string) into a [binary data object](datatypes.md#binobjects)

#### Returns
[binary data object](datatypes.md#binobjects)

### fromBase64(data)
Convert a base64 representation of data into a [binary data object](datatypes.md#binobjects)

#### Returns
[binary data object](datatypes.md#binobjects)

### binaryBlobFromText(txt)
Convert text into a [binary data object](datatypes.md#binobjects)

#### Returns
[binary data object](datatypes.md#binobjects)

### generateQRCode(data)
Encode the specified text data as a QR code image in png format.

#### Returns
[binary data object](datatypes.md#binobjects)


<a name='metadataobject'></a>

## model
### isInstance()
Returns true if the object represents an model instance (as opposed to a model)

#### Returns
bool

<a name='jsdeactivate'></a>

### deactivate()
Deactivate the current instance. Only works when the current object is an model instance

<a name='setAttribute'></a>

### setAttribute(name,value)
Asynchronously  the attribute `name` with the value `value` in the current model instance
This function returns a promise that will complete once the attribute value is set.


<a name='getAttribute'></a>

### getAttribute(name)
Gets the value of the specified attribute in the model instance.
Has no effect when run on a model.

This function returns a promise that will resolve to the attribute's value once the operation completes.

Example:

```

    var p = instance.getAttribute('UserName');
    p.then(user => runtime.done({UserID:user}));

```


#### Returns
Promise<object>


### queryDataSource(datasource, arguments)
Query the datasource named `datasource` in the current object's model's linked UI.
Pass `arguments` as parameters to the data source.

#### Returns
[result set](datatypes.md#dt-results)


<a name='executeAction'></a>

### executeAction(action, object arguments)
Asynchronously execute an action named `action` on the current object, passing `arguments` as parameters.

This method will return a Promise that will resolve to the result of the action upon completion.

#### Returns
Promise<[dictionary](datatypes.md#dictionaries)>