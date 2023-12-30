

[javascriptlib:](javascriptlib:)

# Javascript Library


The following javascript functions are available for use with the |javascript| block.

[jsoi:](jsoi:)
## oi

### model(name)
Creates a new [model reference](metadataobject) for the model with the given name

#### Returns
[MetadataObject](MetadataObject)

### createInstance(model,instanceName)
Create a new model instance of a model and give it a name.

#### Returns
MetadataObject

### setOutput(key, value)
Sets an output for an action.

{% hint style="seealso" %}

    [actionoutput-ref](actionoutput-ref)

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
    [Valid Date/Time Formats](datetimeformats) {% endhint %}


#### Returns
[timestamp](datetimes)

[legacygenexcel:](legacygenexcel:)

### generateExcelSheet(columns, items)
Generate an excel sheet in xlsx format.
Adds column headers and rows of data.

.. list-table::
    :header-rows: 0

    * - code/columns
      - An array of column headers to add to the top.
    * - code/items
      - An array of objects to be populated as rows. Each object should have fields matching the items in the code/columns array

Example:

. code::

    var columns = ['First Name','Last Name','Age'];
    var data = [
        {'First Name':'Ricky','Last Name':'Ricardo','Age':36},
        {'First Name':'Ethel','Last Name':'Mertz','Age':34},
        {'First Name':'Fred','Last Name':'Mertz','Age':48}
    ];
    var sheet = oi.generateExcelSheet(columns,data);


#### Returns
[binary data object](binobjects) - the excel sheet as a binary data stream

### currentUser()
Get attributes about the current logged-in user.

#### Returns
[dictionary](dictionaries) - a dictionary of attributes for the user.
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
[timestamp](datetimes)

[legacyjstzfunctions:](legacyjstzfunctions:)

### convertFromUtc(dt, tz)
Converts a [timestamp](datetimes) from utc to a different timezone.

.. list-table::
    :header-rows: 0

    * - code/dt
      - A [timestamp](datetimes) to convert to a different timezone

    * - code/tz
      - The [code](timezonecodes) of the timezone to convert to

{% hint style="seealso" %}

    [Working with time zones](timezones)

{% endhint %}

    [Time Zone Codes](timezonecodes)

#### Returns
[timestamp](datetimes) converted to a different time zone

### convertToUtc(now, tz)
Converts a [timestamp](datetimes) to utc from a different timezone.

.. list-table::
    :header-rows: 0

    * - code/dt
      - A [timestamp](datetimes) to convert to UTC

    * - code/tz
      - The [code](timezonecodes) of the timezone the [timestamp](datetimes) was currently in.

{% hint style="seealso" %}

    [Working with time zones](timezones)

{% endhint %}

    [Time Zone Codes](timezonecodes)

#### Returns
[timestamp](datetimes) converted to a different time zone

### dateOnly(now)
Returns the date only with the time stripped out.

#### Returns
[timestamp](datetimes)

### escapeXml(name)
Escapes the character sequences suitable for embedding in xml.

#### Returns
string

### isInstance()
Returns true if the current action sequence is executing in an model instance (as opposed to a model)

#### Returns
bool

### executeService(service)
Execute an iviva service

#### Returns
[result set](dt-results)

### executeService(service,parameters)
Execute an iviva service, passing the given parameters

#### Returns
[result set](dt-results)

### guid()
Generate a globally unique identifier.

#### Returns
string

[legacyuploadData:](legacyuploadData:)

### uploadData(name, data)
Upload the given data to the iviva storage, using code/name as a base name.  The actual name used to store the data will be unique and randomly generated using code/name as part of it.
This is to gaurantee no collisions with existing files.

The actual name used to store the data is returned.
This name can be accessed via an http url of the form:

    http://<ivivacloudurl>/content/OI/<filename>

.. list-table::
    :header-rows: 0

    * - code/name
      - The base name for the file
    * - code/data
      - [binary data object](binobjects) representing the data to be uploaded.


#### Returns
string - the actual file name that the data is saved as.

### uploadDataWithExplicitName(name, data)
Same as [uploadData](uploadData) except the name specified is the exact name used to save the file. No extra unique postfix is added to the name.

{% hint type="warning" %}
    This could potentially cause existing uploads to be overwritten if not used carefully. Do not use this function unless you have a very good reason for maintaining file names. {% endhint %}

#### Returns
string

### parseDataURI(uri)
Parse a data uri (specified as a string) into a [binary data object](binobjects)

#### Returns
[binary data object](binobjects)

### fromBase64(data)
Convert a base64 representation of data into a [binary data object](binobjects)

#### Returns
[binary data object](binobjects)

### binaryBlobFromText(txt)
Convert text into a [binary data object](binobjects)

#### Returns
[binary data object](binobjects)

### generateQRCode(data)
Encode the specified text data as a QR code image in png format.

#### Returns
[binary data object](binobjects)


[legacymetadataobject:](legacymetadataobject:)

## model
### isInstance()
Returns true if the object represents an model instance (as opposed to a model)

#### Returns
bool

[legacyjsdeactivate:](legacyjsdeactivate:)

### deactivate()
Deactivate the current instance. Only works when the current object is an model instance

### setAttribute(name, value)
Sets the attribute code/name with the value code/value in the current model instance
Has no effect when run on a model.


### getAttribute(name)
Gets the value of the specified attribute in the model instance.
Has no effect when run on a model.

#### Returns
object


### queryDataSource(datasource, arguments)
Query the datasource named code/datasource in the current object's model's linked UI.
Pass code/arguments as parameters to the data source.

#### Returns
[result set](dt-results)


### executeAction(action, object arguments)
Execute an action named code/action on the current object, passing code/arguments as parameters.

#### Returns
[dictionary](dictionaries)