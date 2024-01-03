


<a name='datasources'></a>

# Working with Data Sources
Data Sources are the central mechanism for gathering data.
You can design data sources to select the attributes you need, filter out data, group and sort them.
You can use data sources to gather data from instances of your models, from objects in iviva or a combination of both.

## Defining Data Sources
You can define data sources using the **DataSource** tab of the [UI Composer](uicomposer).

<figure><img src=' images/datasource.png'></figure>

Start by specifying a name for the data source.
The next step is to specify a *base model* for your source.
The base model can either be an iviva object type or one of your Lucy models.

The base model is the starting point from where you start picking out what fields/attributes you want to examine and how you want to filter or group them.

## Selecting fields for your source
Click the *Select a field* link to select fields you want to add to your data source.

This will invoke a dialog in which all fields of the base model are listed.

{% hint type="note" %}
    If the base model is a Lucy model, then all attributes of the model will be listed along with several standard fields like code/Name, code/Description, code/Key and code/IsActive
    See [instanceattrs](instanceattrs) for more information about attributes. {% endhint %}

You can select fields from either the base model or from any models connected to it. Connected models show up as bold color items, listed after the model's attributes.
You an click them to expand them to see the connected model's own attributes.
You can further find models connected to *that* model, and expand further, picking out attributes as deep as you would like.

.. waring::
    While there is no limit on deep through the model hierarchy you want to go to pull out fields for your data source, keep in mind that the deeper you go, the less performant the query will be.

If you hover your mouse over an attribute, you can get a tooltip showing you the full connection path of that attribute.
Click the image:: images/trash.png icon to delete an attribute.
By default the name of the attribute is the actual attribute's name.
However, in some cases,where you select multiple attributes that have the same name (for example, you select the code/Key attribute of the base model as well as the code/Key attribute of a connected model), then a number (1,2,...) will be appended to the attribute name. For clarity, you can edit the attribute name to change it to something more meaninful and easy to remember.
Click the image:: images/pencil.png icon to edi the attribute name and give it a different name.

{% hint type="note" %}
    Attribute names should be alphanumeric and not contain any spaces {% endhint %}

### Understanding connected models
So what's a connected model?
In the case of Lucy models, any time you define an attribute that represent an object (either an iviva object or another Lucy model), a connection is formed from your model to the one defined by the attribute.

For example, if your model defines an attribute that holds an iviva Location, then there is a connection between your model and the iviva Location object.
The name of that connection is the name you gave to that attribute.

In the case of iViva objects, the connections are defined internally in the iViva application.


## Filtering out results
You can define conditions in your data source and filter out data that doesn't meet those conditions.

In the **Conditions** section in the UI, you can define one or more conditions.
If multiple conditions are defined, *all* of them must be met for the data to be selected.

For each condition, you can specify an attribute that the condition will apply to. You can only select attributes that you have aleady selected.

Then specify the operator to use for checking the condition.
Depending on the operator, you may need to specify another field or value.

The following operators are available:

### Exists
Returns true if the specified attribute has a value that is not null or an [empty value](emptyvalues).

### Does not exist
Returns true if the specified attribute has a value that is null or an [empty value](emptyvalues).

### Equals
Returns true if the specified attribute hasa value equal to the value specified in the second text box. You can use [parameters](datasourceparameters) in the second text box to specify that the value should be taken from an input parameter.

### Not Equal To
Returns true if the specified attribute is not equal to the value specified in the second text box.
You can use [parameters](datasourceparameters) in the second text box to specify that the value should be taken from an input parameter.

### Contains
Returns true if the specified attribute is one of the values specified in the second text box. The second text box must contain a comma separated list of possible values. You can use [parameters](datasourceparameters) in the second text box to specify that the values to check against should be taken from an input parameter.

### Contains Text
Returns true if the specified attribute contains the text specified in the second text box. The match does not have to be exact. If the specified text is contained anywhere within the attribute value, it will match.
You can use [parameters](datasourceparameters) in the second text box to specify that the value should be taken from an input parameter.

### Include in text search
If an attribute is specified with this option, then this attributed is checked against a global text parameter, defined by a parameter named code/q to see if it matches.
This is different from the *Contains Text* operator in that multiple attributes can be selected for inclusion in text search and if *any* of them match the text specified by the code/q parameter, then that result is considered a match.

### Greater Than
Checks if the attribute is greater than the value specified in the second text box.
You can use [parameters](datasourceparameters) in the second text box to specify that the value should be taken from an input parameter.
This is only available for attributes that represent numbers or [timestamp](datetimes) values.

### Less Than
Checks if the attribute is less than the value specified in the second text box.
You can use [parameters](datasourceparameters) in the second text box to specify that the value should be taken from an input parameter.
This is only available for attributes that represent numbers or [timestamp](datetimes) values.

### Is Within Location
This operator is only available when the attribute represents a valid iviva Location Key. This operator matches if the location represented by the attribute is a child location (or an exact match) of the location specified in the second text box.
You can use [parameters](datasourceparameters) in the second text box to specify that the value should be taken from an input parameter.
The value in the second text box should be a number representing the key of a parent location.


<a name='emptyvalues'></a>
## Dealing with Empty Values
Some conditional operators check if the attibute has an empty value or not.
What is an empty value?
It depends on the type of the attribute.
For text attributes, empty strings constitute empty values.
For number attributes, 0 consitutes empty values.
For object references, a key with a value of `0` constitutes an empty value.


## Deleting, Renaming and Copying Sources
Datasources cannot be renamed. However, they can be duplicated by clicking the 'Duplicate this data source' link and specifying a name for the new source.
Datasources can be deleted by clicking the 'Delete this Data Source' link.

{% hint type="warning" %}
    You will not get a notification if you try to delete a datasource that is already in use in a UI screen or called from a |calldatasource| block.
    Delete datasources with care only after making sure they are not used! {% endhint %}

## Working with Input Parameters
Datasources that return the same set of data each time they are called are only semi-useful. In most cases, you will want to pass inputs to the source to determine how and what it should query for results.
Input parameters can be used as part of the list of conditions you specify to control what results you get.

To specify input parameters to the data source, first add it to the parameter list.

Click the 'Add Parameter' link in the **Parameters** section and specify a name for the parameter.

Then, in the **Conditions** section, in any of the textboxes that expect a value to compare an attribute with, enter the parameter name prefixed by a code/$ symbol.
So if you use a parameter called code/key, then in the condition's value text box, use code/$key as the value.

{% hint type="note" %}
    Since parameter names will often map directly to page query strings or other forms of inputs, its best that parameters are limited to alphanumeric characters only {% endhint %}


<a name='datasourceparameters'></a>

## Specifying input parameter values
When querying a data source, you need to specify values for the actual parameters. How you do this depends on how the data source is used.

1. Calling a source from a |calldatasource| block: Specify the parameters as input pins to the block and the values written to those pins are the values passed to the data source

2. Calling the source from a UI screen - The page inputs are typically passed directly into all data sources - so using page inputs you can control the parameters passed to the data source

3. Calling a source from a [celllist-ref](celllist-ref). In this case, the list of inputs to the data source are explicitly specified when configuring the [celllist-ref](celllist-ref).

{% hint type="note" %}
    Since a common use-case of filters is to filter by the current logged-in user, in addition to accepting code/$parameter syntax in the conditions, you can also specify code/#{auth.UserKey} to denote that the logged-in user's UserKey should be used in that place. {% endhint %}

## Previewing Data Sources
You can preview your datasource by hitting the **Preview** button at the top of the page.

A few things to keep in mind about the preview:

1. The preview only returns the first 10 records that matched
2. The preview does not take into account any input parameters. These parameters are not passed to the preview screen. So if you have code/Required set in any of the conditions, and they contain input parameters, you will not get any results.