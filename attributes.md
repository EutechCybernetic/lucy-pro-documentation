

<a name='attributes'></a>

# Attributes
Attributes are basically pieces of metadata that you associate with your model.
They are what you would use to uniquely identify your objects.
You can define as many or as few attributes as you want for your model.
These attributes can store virtually any type of data - free form text, numbers, dates, timestamps, or even references to other models or objects.

Taking the example of an **Asset** model, you may define the following attributes for it:

- AssetID - some piece of text that uniquely identifies each asset - like a serial number
- Manufacturer - the name of the manufacturer of the asset
- PurchaseDate - the timestamp of when the asset was purchased.
- Owner - this is a reference to a *different* model - an **Employee** model in this case. It represents who the owner of this Asset is.

Attributes are defined in each model. The data that is associated with each attribute is specified in each actual model instance of the model.



|Data type|Description|
|--|--|
|Text|Represents any generic piece of data - a name, a number, a JSON payload etc...|
|DateTime|Used to represent a time stamp, a day, or a time.|
 

        Can be used with the various date manipulation blocks in Lucy.

        All date times are stored in UTC internally
    * - *References*
      - A reference to any other object in the system - either an iviva application object or another Lucy model. Internally, these are stored using a *type* which denotes the type of object being saved, and a key (an integer) that uniquely identifies that particular object within a given type.

{% hint type="seealso" %}
    [Attr Editor](modeldesigner.md#attributeeditor) {% endhint %}

{% hint type="seealso" %}
    [Working with Dates and Times](datatypes.md#datetimes) {% endhint %}