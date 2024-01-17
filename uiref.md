
<a name='fieldblock-widget'></a>

# Vertical Layout
A container in which ui elements can be placed vertically, one below another.
Each ui element dropped into this field will be stacked vertically below the previous one.
Drag the ui element around to re-arrange the order in which they are displayed.

## Appearance Properties



|Property|Description|
|--|--|
|Color Scheme|The color scheme to use for the background of this container.|
|Visible|Controls whether the ui element is actually visible on the screen. If this is set to false, then the ui element is never rendered to the screen. This is property is useful only if you want to permanently hide a ui element (maybe beacuse you temporarily don't want to show it to anyone). If you want to control the visibility of a ui element based on some logic, use the VisibilityExpression property.|
|Visibility Expression|You can specify an [iviva Expression](ice.md#ice) expression here which should evaluate to true if you want the ui element to be shown. It should evaluate to false if the ui element should be hidden.
## General Properties|
 



|Property|Description|
|--|--|
|Auto Update|This property is currently not used.|
|id|An identifier for this ui element|
|tag|The tag is an identifier you can associate with the widget. This is used to identify the element in client-side javascript. See [Accessing widgets from javascript](uis.md#uitags) for more information on how and where to use them.
## Position Properties|
 



|Property|Description|
|--|--|
|Bottom|The position of the ui element relative to the bottom-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Height|The height of the ui element See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned and sized.|
|Left|The position of the ui element relative to the left-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Right|The position of the ui element relative to the right-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Top|The position of the ui element relative to the top-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Width|The width of the ui element See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned and sized.
<a name='fieldline-widget'></a>|
 

# Horizontal Layout
A container in which ui elements can be placed horizontally, one next to another.
Each ui element dropped into this field will be stacked horizontally just after the previous one.
Drag the ui element around from left-toright to re-arrange the order in which they are displayed.

This container is useful for arranging a sequence of buttons together on a single row.

## Appearance Properties



|Property|Description|
|--|--|
|Color Scheme|The color scheme to use for the background of this container.|
|Visible|Controls whether the ui element is actually visible on the screen. If this is set to false, then the ui element is never rendered to the screen. This is property is useful only if you want to permanently hide a ui element (maybe beacuse you temporarily don't want to show it to anyone). If you want to control the visibility of a ui element based on some logic, use the VisibilityExpression property.|
|Visibility Expression|You can specify an [iviva Expression](ice.md#ice) expression here which should evaluate to true if you want the ui element to be shown. It should evaluate to false if the ui element should be hidden.
## General Properties|
 



|Property|Description|
|--|--|
|Auto Update|This property is currently not used.|
|id|An identifier for this ui element|
|tag|The tag is an identifier you can associate with the widget. This is used to identify the element in client-side javascript. See [Accessing widgets from javascript](uis.md#uitags) for more information on how and where to use them.
## Position Properties|
 



|Property|Description|
|--|--|
|Bottom|The position of the ui element relative to the bottom-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Height|The height of the ui element See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned and sized.|
|Left|The position of the ui element relative to the left-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Right|The position of the ui element relative to the right-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Top|The position of the ui element relative to the top-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Width|The width of the ui element See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned and sized.
<a name='label-widget'></a>|
 

# Label
Displays a simple text label on the screen.
The label's text property can be [data bound](uis.md#databinding).

## Appearance Properties



|Property|Description|
|--|--|
|Text Alignment|Specifies how text should be aligned. Available options are `right`, `left` or `center` for right-alignment, left-alignment or center-alignment. This only affects horizontal alignment of text. The default is left-alignment.|
|Color|The color for the text. You can select from one of several predefined colors.|
|Text Size|Controls the size of the text. There are several predefined sizes to choose from. These sizes are pre-determined based on the iviva theme.|
|Text Weight|Controls the weight of the font used. You can choose between `normal`, `bold` and `bolder`|
|No Data Text|The text to be shown when no data is bound. This can be any free-form text or it could embed an [iviva Expression](ice.md#ice).|
|Text|The text associated with this element. This can be any free-form text or it could be an [iviva Expression](ice.md#ice) to bind data.|
|Prominence|Controls whether the text should be shown prominently or subdued. Use subdued text for labels and for data which isn't very important. Set this to `subdued` to give contrast with other pieces of text nearby that are more important.|
|Visible|Controls whether the ui element is actually visible on the screen. If this is set to false, then the ui element is never rendered to the screen. This is property is useful only if you want to permanently hide a ui element (maybe beacuse you temporarily don't want to show it to anyone). If you want to control the visibility of a ui element based on some logic, use the VisibilityExpression property.|
|Visibility Expression|You can specify an [iviva Expression](ice.md#ice) expression here which should evaluate to true if you want the ui element to be shown. It should evaluate to false if the ui element should be hidden.
## General Properties|
 



|Property|Description|
|--|--|
|Auto Update|This property is currently not used.|
|id|An identifier for this ui element|
|tag|The tag is an identifier you can associate with the widget. This is used to identify the element in client-side javascript. See [Accessing widgets from javascript](uis.md#uitags) for more information on how and where to use them.
## Position Properties|
 



|Property|Description|
|--|--|
|Bottom|The position of the ui element relative to the bottom-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Height|The height of the ui element See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned and sized.|
|Left|The position of the ui element relative to the left-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Right|The position of the ui element relative to the right-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Top|The position of the ui element relative to the top-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Width|The width of the ui element See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned and sized.
<a name='objectlink-widget'></a>|
 

# Object Link
This ui element renders an object as a link. Clicking the link will either
navigate to the object's details screen or will show a quick-info bubble about that object.

The ObjectKey property can be [data bound](uis.md#databinding) to any object key field from a data source.
However, when binding the key, the corresponding object's text field must also be available in the data source.

If that's not the case, or if you wish to use a different field to represent text, then you will have to manually bind data by explicitly specifying
the ObjectKey, ObjectType and ObjectID fields.

##  Properties



|Property|Description|
|--|--|
|Text|The text associated with this element. This can be any free-form text or it could be an [iviva Expression](ice.md#ice) to bind data.
## Appearance Properties|
 



|Property|Description|
|--|--|
|Text Alignment|Specifies how text should be aligned. Available options are `right`, `left` or `center` for right-alignment, left-alignment or center-alignment. This only affects horizontal alignment of text. The default is left-alignment.|
|Color|The color for the text. You can select from one of several predefined colors.|
|Text Size|Controls the size of the text. There are several predefined sizes to choose from. These sizes are pre-determined based on the iviva theme.|
|Text Weight|Controls the weight of the font used. You can choose between `normal`, `bold` and `bolder`|
|No Data Text|The text to be shown when no data is bound. This can be any free-form text or it could embed an [iviva Expression](ice.md#ice).|
|Prominence|Controls whether the text should be shown prominently or subdued. Use subdued text for labels and for data which isn't very important. Set this to `subdued` to give contrast with other pieces of text nearby that are more important.|
|Visible|Controls whether the ui element is actually visible on the screen. If this is set to false, then the ui element is never rendered to the screen. This is property is useful only if you want to permanently hide a ui element (maybe beacuse you temporarily don't want to show it to anyone). If you want to control the visibility of a ui element based on some logic, use the VisibilityExpression property.|
|Visibility Expression|You can specify an [iviva Expression](ice.md#ice) expression here which should evaluate to true if you want the ui element to be shown. It should evaluate to false if the ui element should be hidden.
## General Properties|
 



|Property|Description|
|--|--|
|Auto Update|This property is currently not used.|
|id|An identifier for this ui element|
|Include Icon|Determines whether or not to render an icon next to the object text. The icon used will depend on the object type.|
|Link Type|This can either be `Quick Info` or `Navigate` to indicate whether clicking the link should navigate to the object's details screen or just show a quick-info bubble for the object on the current page itself.|
|Object Key|The unique key of the object being shown|
|Object Type|The type of the object being represented by the link. This will determine what page to navigate to, what quick info bubble to show and what icon to show.|
|tag|The tag is an identifier you can associate with the widget. This is used to identify the element in client-side javascript. See [Accessing widgets from javascript](uis.md#uitags) for more information on how and where to use them.
## Position Properties|
 



|Property|Description|
|--|--|
|Bottom|The position of the ui element relative to the bottom-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Height|The height of the ui element See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned and sized.|
|Left|The position of the ui element relative to the left-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Right|The position of the ui element relative to the right-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Top|The position of the ui element relative to the top-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Width|The width of the ui element See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned and sized.
<a name='icon-widget'></a>|
 

# Icon
This element displays an icon on the screen.
iviva ships hundres of vector-based icons. You can select one of them to be used.
Icons can also be clicked on to invoke actions.
The font-size property controls the size of the icon.

## Actions Properties



|Property|Description|
|--|--|
|actions|The list of [User Interface Actions](uis.md#uiactions) to execute when the icon is clicked.
## Appearance Properties|
 



|Property|Description|
|--|--|
|Color|The color for the text. You can select from one of several predefined colors.|
|Text Size|Controls the size of the text. There are several predefined sizes to choose from. These sizes are pre-determined based on the iviva theme.|
|icon|Display an icon from a pre-defined list. iviva ships with several hundred vector-based icons. You can select from them to be used.|
|Visible|Controls whether the ui element is actually visible on the screen. If this is set to false, then the ui element is never rendered to the screen. This is property is useful only if you want to permanently hide a ui element (maybe beacuse you temporarily don't want to show it to anyone). If you want to control the visibility of a ui element based on some logic, use the VisibilityExpression property.|
|Visibility Expression|You can specify an [iviva Expression](ice.md#ice) expression here which should evaluate to true if you want the ui element to be shown. It should evaluate to false if the ui element should be hidden.
## General Properties|
 



|Property|Description|
|--|--|
|Auto Update|This property is currently not used.|
|id|An identifier for this ui element|
|tag|The tag is an identifier you can associate with the widget. This is used to identify the element in client-side javascript. See [Accessing widgets from javascript](uis.md#uitags) for more information on how and where to use them.
## Position Properties|
 



|Property|Description|
|--|--|
|Bottom|The position of the ui element relative to the bottom-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Height|The height of the ui element See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned and sized.|
|Left|The position of the ui element relative to the left-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Right|The position of the ui element relative to the right-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Top|The position of the ui element relative to the top-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Width|The width of the ui element See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned and sized.
<a name='celllist-widget'></a>|
 

# Search Results
This ui element is used to show a dynamic, scrolling set of results from a [data source](datasources.md#datasources).
When bound to a datasource, it will pull in items to display in a scrollable area.
As you scroll down, more items are pulled in. This makes it an effecient mechanism for displaying
and browsing through a large list of items.

Further more, the datasource used can take input parameters that are linked to other ui elements in the screen.
When those ui elements change their values, the datasource is automatically requeried with the new set of values
and the results are refreshed to reflected the changed data.

This makes this ui element suitable for displaying search results with filters that can be set by the user.

See [Working with lists of items](uis.md#uilists) for more information.

This is similar to a [repeater-widget](repeater-widget) except that here

1. only a few items are shown at once and more are pulled in as the user scrolls through the list
2. The height of the list is fixed and any extra content is hidden and needs to be scrolled to be seen
3. the datasource can take parameters that change dynamically.

This ui element is useful for showing a large list of items efficiently.
However, it cannot be used to show data entry fields that require data to be captured.
This is because the ids of the data entry fields will keep changing as the list scrolls, making it difficult to capture information.
Instead, consider using a [Action](uiref.md#action-widget) or [Icon](uiref.md#icon-widget) in the results that
display a dialog when clicked, in which the user can edit and save details about a particular item.

## Appearance Properties



|Property|Description|
|--|--|
|Hide `Empty` text|Set this to explicitly hide the 'No results' message when there is no data to be shown|
|Hide `End of Results` text|Set this to explicitly hide the 'No more results' message when the end of the list is reached.|
|Empty Text|The message to show when there is no results in the data source Defaults to 'No results' if nothing is set.|
|End of results text|Message to be shown after the last result is pulled in and dispalyed. Defaults to 'No more results' if nothing is specified here.|
|Visible|Controls whether the ui element is actually visible on the screen. If this is set to false, then the ui element is never rendered to the screen. This is property is useful only if you want to permanently hide a ui element (maybe beacuse you temporarily don't want to show it to anyone). If you want to control the visibility of a ui element based on some logic, use the VisibilityExpression property.|
|Visibility Expression|You can specify an [iviva Expression](ice.md#ice) expression here which should evaluate to true if you want the ui element to be shown. It should evaluate to false if the ui element should be hidden.
## Datasource Properties|
 



|Property|Description|
|--|--|
|datasource|The [data source](datasources.md#datasources) to bind to for showing results.
## General Properties|
 



|Property|Description|
|--|--|
|Auto Update|This property is currently not used.|
|id|An identifier for this ui element|
|Item Height|The height, in pixels of each row of the results.|
|tag|The tag is an identifier you can associate with the widget. This is used to identify the element in client-side javascript. See [Accessing widgets from javascript](uis.md#uitags) for more information on how and where to use them.
## Position Properties|
 



|Property|Description|
|--|--|
|Bottom|The position of the ui element relative to the bottom-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Height|The height of the ui element See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned and sized.|
|Left|The position of the ui element relative to the left-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Right|The position of the ui element relative to the right-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Top|The position of the ui element relative to the top-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Width|The width of the ui element See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned and sized.
<a name='dynamiclist-widget'></a>|
 

# Object Picker
This ui element is used to select an element from a list.
This is similar to a [List Box](uiref.md#list-widget) except that the list of items to select from
is dynamically populated from a data source or from a list of pre-defined objects.
You must specify either
* a model to bind to
* or a datasource to bind to

## Appearance Properties



|Property|Description|
|--|--|
|Value|The value of the element. This can be any free-form text or it could embed an [iviva Expression](ice.md#ice).|
|Visible|Controls whether the ui element is actually visible on the screen. If this is set to false, then the ui element is never rendered to the screen. This is property is useful only if you want to permanently hide a ui element (maybe beacuse you temporarily don't want to show it to anyone). If you want to control the visibility of a ui element based on some logic, use the VisibilityExpression property.|
|Visibility Expression|You can specify an [iviva Expression](ice.md#ice) expression here which should evaluate to true if you want the ui element to be shown. It should evaluate to false if the ui element should be hidden.
## Datasource Properties|
 



|Property|Description|
|--|--|
|datasource|A [data source](datasources.md#datasources) to be used to populate the list. If this is set, the Key Field and Text Field properties must also be set to determine which field from the datasource represents the *value* of the ui element and which field represents text which is displayed in the ui element. To make the datasource filter its data by the text that is typed, you can add a text filter to the datasource which filters by a parameter named `q` The field will pass the typed-in text as the `q` parameter when querying the data source.|
|Key Field|The field from the datasource that is used to represent the value of the selected item.|
|Text Field|The field from the datasource that gets displayed on screen for each item in the datasource results.
## General Properties|
 



|Property|Description|
|--|--|
|Auto Update|This property is currently not used.|
|id|An identifier for this ui element|
|Object Type|Bind this list to a particular object type to show all objects of that type to the user. The object's key property will be used as the selected value.|
|tag|The tag is an identifier you can associate with the widget. This is used to identify the element in client-side javascript. See [Accessing widgets from javascript](uis.md#uitags) for more information on how and where to use them.
## Position Properties|
 



|Property|Description|
|--|--|
|Bottom|The position of the ui element relative to the bottom-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Height|The height of the ui element See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned and sized.|
|Left|The position of the ui element relative to the left-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Right|The position of the ui element relative to the right-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Top|The position of the ui element relative to the top-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Width|The width of the ui element See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned and sized.
<a name='list-widget'></a>|
 

# List Box
This ui element shows a simple list of items from which one can be selected.
The Value property can be [data bound](uis.md#databinding) and have it  auto-select an item when the screen is shown.

The list of items to use can be specified in four ways:

1. A simple list - you can specify a comma separated list of possible values. Put the text into the `Items` property.
For example,

```
    Yes,No```

2. A json dictionary of key/text pairs. The key represents the internal value. The text represents what is displayed in the list.
Put the json definition into the `Items` property.
For example,

```
    {'1':'Yes, do it!','0':'Nah, forget it'}```

3. An object type - specify the `Object Type` property. A list of all objects of that type will be shown in the list.
The Value property is represented by the object's key.

4. A data source - You can bind a [data source](datasources.md#datasources) to a list. Specify which field represents the key and which represents
the text to be shown.


##  Properties



|Property|Description|
|--|--|
|Value|The value of the element. This can be any free-form text or it could embed an [iviva Expression](ice.md#ice).
## Appearance Properties|
 



|Property|Description|
|--|--|
|Visible|Controls whether the ui element is actually visible on the screen. If this is set to false, then the ui element is never rendered to the screen. This is property is useful only if you want to permanently hide a ui element (maybe beacuse you temporarily don't want to show it to anyone). If you want to control the visibility of a ui element based on some logic, use the VisibilityExpression property.|
|Visibility Expression|You can specify an [iviva Expression](ice.md#ice) expression here which should evaluate to true if you want the ui element to be shown. It should evaluate to false if the ui element should be hidden.
## Datasource Properties|
 



|Property|Description|
|--|--|
|Items|Either a comma separated list of items in the list, or a JSON dictionary representing the items.|
|Key Field|The field from the datasource that is used to represent the value of the selected item.|
|Object Type|Bind this list to a particular object type to show all objects of that type to the user. The object's key property will be used as the selected value.|
|Data Source|A [data source](datasources.md#datasources) to be used to populate the list. If this is set, the Key Field and Text Field properties must also be set to determine which field from the datasource represents the *value* of the ui element and which field represents text which is displayed in the ui element. To make the datasource filter its data by the text that is typed, you can add a text filter to the datasource which filters by a parameter named `q` The field will pass the typed-in text as the `q` parameter when querying the data source.|
|Text Field|The field from the datasource that gets displayed on screen for each item in the datasource results.
## General Properties|
 



|Property|Description|
|--|--|
|Auto Update|This property is currently not used.|
|Empty Text|The text to be shown when nothing is selected. This is typically the first item shown in the list.|
|id|An identifier for this ui element|
|tag|The tag is an identifier you can associate with the widget. This is used to identify the element in client-side javascript. See [Accessing widgets from javascript](uis.md#uitags) for more information on how and where to use them.
## Position Properties|
 



|Property|Description|
|--|--|
|Bottom|The position of the ui element relative to the bottom-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Height|The height of the ui element See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned and sized.|
|Left|The position of the ui element relative to the left-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Right|The position of the ui element relative to the right-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Top|The position of the ui element relative to the top-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Width|The width of the ui element See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned and sized.
<a name='text-widget'></a>|
 

# Text
A text input field where users can type in any text.
The Text property can be [data bound](uis.md#databinding).

## Appearance Properties



|Property|Description|
|--|--|
|Text|The text associated with this element. This can be any free-form text or it could be an [iviva Expression](ice.md#ice) to bind data.|
|Visible|Controls whether the ui element is actually visible on the screen. If this is set to false, then the ui element is never rendered to the screen. This is property is useful only if you want to permanently hide a ui element (maybe beacuse you temporarily don't want to show it to anyone). If you want to control the visibility of a ui element based on some logic, use the VisibilityExpression property.|
|Visibility Expression|You can specify an [iviva Expression](ice.md#ice) expression here which should evaluate to true if you want the ui element to be shown. It should evaluate to false if the ui element should be hidden.
## General Properties|
 



|Property|Description|
|--|--|
|Auto Update|This property is currently not used.|
|id|An identifier for this ui element|
|tag|The tag is an identifier you can associate with the widget. This is used to identify the element in client-side javascript. See [Accessing widgets from javascript](uis.md#uitags) for more information on how and where to use them.
## Position Properties|
 



|Property|Description|
|--|--|
|Bottom|The position of the ui element relative to the bottom-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Height|The height of the ui element See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned and sized.|
|Left|The position of the ui element relative to the left-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Right|The position of the ui element relative to the right-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Top|The position of the ui element relative to the top-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Width|The width of the ui element See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned and sized.
<a name='hidden-widget'></a>|
 

# Hidden
This ui element does not display any user interface.
Its main use is to hold a piece of data to be accessed by client-side javascript on the page.

##  Properties



|Property|Description|
|--|--|
|Value|The value of the element. This can be any free-form text or it could embed an [iviva Expression](ice.md#ice).
## Appearance Properties|
 



|Property|Description|
|--|--|
|Visible|Controls whether the ui element is actually visible on the screen. If this is set to false, then the ui element is never rendered to the screen. This is property is useful only if you want to permanently hide a ui element (maybe beacuse you temporarily don't want to show it to anyone). If you want to control the visibility of a ui element based on some logic, use the VisibilityExpression property.|
|Visibility Expression|You can specify an [iviva Expression](ice.md#ice) expression here which should evaluate to true if you want the ui element to be shown. It should evaluate to false if the ui element should be hidden.
## General Properties|
 



|Property|Description|
|--|--|
|Auto Update|This property is currently not used.|
|id|An identifier for this ui element|
|tag|The tag is an identifier you can associate with the widget. This is used to identify the element in client-side javascript. See [Accessing widgets from javascript](uis.md#uitags) for more information on how and where to use them.
## Position Properties|
 



|Property|Description|
|--|--|
|Bottom|The position of the ui element relative to the bottom-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Height|The height of the ui element See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned and sized.|
|Left|The position of the ui element relative to the left-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Right|The position of the ui element relative to the right-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Top|The position of the ui element relative to the top-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Width|The width of the ui element See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned and sized.
<a name='datetime-widget'></a>|
 

# DateTime
This element lets you edit a [timestamp](datatypes.md#datetimes) value.
Its value property can be [data bound](uis.md#databinding) to a [timestamp](datatypes.md#datetimes) field from a datasource.
The [timestamp](datatypes.md#datetimes) will be displayed in the current logged-in user's timezone

## Appearance Properties



|Property|Description|
|--|--|
|Value|The value of the element. This can be any free-form text or it could embed an [iviva Expression](ice.md#ice).|
|Visible|Controls whether the ui element is actually visible on the screen. If this is set to false, then the ui element is never rendered to the screen. This is property is useful only if you want to permanently hide a ui element (maybe beacuse you temporarily don't want to show it to anyone). If you want to control the visibility of a ui element based on some logic, use the VisibilityExpression property.|
|Visibility Expression|You can specify an [iviva Expression](ice.md#ice) expression here which should evaluate to true if you want the ui element to be shown. It should evaluate to false if the ui element should be hidden.
## General Properties|
 



|Property|Description|
|--|--|
|Auto Update|This property is currently not used.|
|id|An identifier for this ui element|
|tag|The tag is an identifier you can associate with the widget. This is used to identify the element in client-side javascript. See [Accessing widgets from javascript](uis.md#uitags) for more information on how and where to use them.
## Position Properties|
 



|Property|Description|
|--|--|
|Bottom|The position of the ui element relative to the bottom-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Height|The height of the ui element See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned and sized.|
|Left|The position of the ui element relative to the left-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Right|The position of the ui element relative to the right-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Top|The position of the ui element relative to the top-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Width|The width of the ui element See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned and sized.
<a name='date-widget'></a>|
 

# Date
This element lets you edit a date value.
Its value property can be [data bound](uis.md#databinding) to a [timestamp](datatypes.md#datetimes) field from a datasource.
The time property is ignored when bound to a [timestamp](datatypes.md#datetimes) value.

## Appearance Properties



|Property|Description|
|--|--|
|Value|The value of the element. This can be any free-form text or it could embed an [iviva Expression](ice.md#ice).|
|Visible|Controls whether the ui element is actually visible on the screen. If this is set to false, then the ui element is never rendered to the screen. This is property is useful only if you want to permanently hide a ui element (maybe beacuse you temporarily don't want to show it to anyone). If you want to control the visibility of a ui element based on some logic, use the VisibilityExpression property.|
|Visibility Expression|You can specify an [iviva Expression](ice.md#ice) expression here which should evaluate to true if you want the ui element to be shown. It should evaluate to false if the ui element should be hidden.
## General Properties|
 



|Property|Description|
|--|--|
|Auto Update|This property is currently not used.|
|id|An identifier for this ui element|
|tag|The tag is an identifier you can associate with the widget. This is used to identify the element in client-side javascript. See [Accessing widgets from javascript](uis.md#uitags) for more information on how and where to use them.
## Position Properties|
 



|Property|Description|
|--|--|
|Bottom|The position of the ui element relative to the bottom-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Height|The height of the ui element See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned and sized.|
|Left|The position of the ui element relative to the left-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Right|The position of the ui element relative to the right-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Top|The position of the ui element relative to the top-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Width|The width of the ui element See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned and sized.
<a name='time-widget'></a>|
 

# Time
This element lets you edit a time value.
Its value property can be [data bound](uis.md#databinding) to a [timestamp](datatypes.md#datetimes) field from a datasource.
The date property is ignored when bound to a [timestamp](datatypes.md#datetimes) value.

## Appearance Properties



|Property|Description|
|--|--|
|Value|The value of the element. This can be any free-form text or it could embed an [iviva Expression](ice.md#ice).|
|Visible|Controls whether the ui element is actually visible on the screen. If this is set to false, then the ui element is never rendered to the screen. This is property is useful only if you want to permanently hide a ui element (maybe beacuse you temporarily don't want to show it to anyone). If you want to control the visibility of a ui element based on some logic, use the VisibilityExpression property.|
|Visibility Expression|You can specify an [iviva Expression](ice.md#ice) expression here which should evaluate to true if you want the ui element to be shown. It should evaluate to false if the ui element should be hidden.
## General Properties|
 



|Property|Description|
|--|--|
|Auto Update|This property is currently not used.|
|id|An identifier for this ui element|
|tag|The tag is an identifier you can associate with the widget. This is used to identify the element in client-side javascript. See [Accessing widgets from javascript](uis.md#uitags) for more information on how and where to use them.
## Position Properties|
 



|Property|Description|
|--|--|
|Bottom|The position of the ui element relative to the bottom-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Height|The height of the ui element See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned and sized.|
|Left|The position of the ui element relative to the left-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Right|The position of the ui element relative to the right-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Top|The position of the ui element relative to the top-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Width|The width of the ui element See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned and sized.
<a name='checkbox-widget'></a>|
 

# Checkbox
Displays a checkbox.
Use the Value property to bind the checkbox to a value.
Use the CheckedValue and UncheckedValue properties to decide how to intrepret the value.
If the CheckedValue is equal to the Value, then the checkbox will be checked, otherwise it will be unchecked.
Typically, the CheckedValue will be set to `1` and the unchecked value will be set to `0`

##  Properties



|Property|Description|
|--|--|
|Value|The value of the element. This can be any free-form text or it could embed an [iviva Expression](ice.md#ice).
## Appearance Properties|
 



|Property|Description|
|--|--|
|Text|The label for the checkbox|
|Visible|Controls whether the ui element is actually visible on the screen. If this is set to false, then the ui element is never rendered to the screen. This is property is useful only if you want to permanently hide a ui element (maybe beacuse you temporarily don't want to show it to anyone). If you want to control the visibility of a ui element based on some logic, use the VisibilityExpression property.|
|Visibility Expression|You can specify an [iviva Expression](ice.md#ice) expression here which should evaluate to true if you want the ui element to be shown. It should evaluate to false if the ui element should be hidden.
## General Properties|
 



|Property|Description|
|--|--|
|Auto Update|This property is currently not used.|
|Unhecked Value|The value that represents the checkbox's unchecked state. If the checkbox's value property matches this, then the checkbox state will be unchecked. (Actually, the checkbox state will be unchecked as long as the CheckedValue property doesn't match the Value property)|
|id|An identifier for this ui element|
|tag|The tag is an identifier you can associate with the widget. This is used to identify the element in client-side javascript. See [Accessing widgets from javascript](uis.md#uitags) for more information on how and where to use them.|
|Checked Value|The value that represents the checkbox's checked state. If the checkbox's value property matches this, then the checkbox state will be checked.
## Position Properties|
 



|Property|Description|
|--|--|
|Bottom|The position of the ui element relative to the bottom-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Height|The height of the ui element See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned and sized.|
|Left|The position of the ui element relative to the left-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Right|The position of the ui element relative to the right-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Top|The position of the ui element relative to the top-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Width|The width of the ui element See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned and sized.
<a name='fieldlist-widget'></a>|
 

# Field List
A container that's used to layout widgets with titles/labels next to them.
This is similar to a [Vertical Layout](uiref.md#fieldblock-widget) in that ui elements are stacked vertically.
However, in this case, each ui element will also have a title.

Click on the title label to edit it directly in the UI design surface. You can also make it empty to indicate no title should be shown.

Use this container to lay out data entry forms and data display forms easily.

## Appearance Properties



|Property|Description|
|--|--|
|Color Scheme|The color scheme to use for the background of this container.|
|Number of Columns|The number of columns to split the fields into. The default is `1`. If set to more than one, multiple columns will appear on the screen with fields flowing from left to right until the last column is reached and then going down to the next row. This only takes affect if the `Use Vertical Titles` property is set to true. You will not see this updated in the design surface but can see this at run-time.|
|Use Vertical Titles|If set to true, labels are displayed above each field. If set to false, labels are displayed to the left of each field. In general, in iviva, static displays use labels above, whereas data entry forms which expect inputs show labels to the left.|
|Visible|Controls whether the ui element is actually visible on the screen. If this is set to false, then the ui element is never rendered to the screen. This is property is useful only if you want to permanently hide a ui element (maybe beacuse you temporarily don't want to show it to anyone). If you want to control the visibility of a ui element based on some logic, use the VisibilityExpression property.|
|Visibility Expression|You can specify an [iviva Expression](ice.md#ice) expression here which should evaluate to true if you want the ui element to be shown. It should evaluate to false if the ui element should be hidden.
## General Properties|
 



|Property|Description|
|--|--|
|Auto Update|This property is currently not used.|
|id|An identifier for this ui element|
|tag|The tag is an identifier you can associate with the widget. This is used to identify the element in client-side javascript. See [Accessing widgets from javascript](uis.md#uitags) for more information on how and where to use them.
## Position Properties|
 



|Property|Description|
|--|--|
|Bottom|The position of the ui element relative to the bottom-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Height|The height of the ui element See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned and sized.|
|Left|The position of the ui element relative to the left-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Right|The position of the ui element relative to the right-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Top|The position of the ui element relative to the top-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Width|The width of the ui element See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned and sized.
<a name='action-widget'></a>|
 

# Action
A button element that invokes one or more actions when clicked.
This element can be styled as a button or a link.

## Actions Properties



|Property|Description|
|--|--|
|actions|The list of [User Interface Actions](uis.md#uiactions) to execute when the button is clicked.
## Appearance Properties|
 



|Property|Description|
|--|--|
|Button Type|Controls how the button should select. Available choices are: * Normal Button - displays as a regular iviva button * Alternate Button - displays like a cancel button. Use this to specify an alternate and less-used action to be taken * Link - displays the action as a hyper link.|
|Text|The text associated with this element. This can be any free-form text or it could be an [iviva Expression](ice.md#ice) to bind data.|
|Visible|Controls whether the ui element is actually visible on the screen. If this is set to false, then the ui element is never rendered to the screen. This is property is useful only if you want to permanently hide a ui element (maybe beacuse you temporarily don't want to show it to anyone). If you want to control the visibility of a ui element based on some logic, use the VisibilityExpression property.|
|Visibility Expression|You can specify an [iviva Expression](ice.md#ice) expression here which should evaluate to true if you want the ui element to be shown. It should evaluate to false if the ui element should be hidden.
## General Properties|
 



|Property|Description|
|--|--|
|Auto Update|This property is currently not used.|
|id|An identifier for this ui element|
|tag|The tag is an identifier you can associate with the widget. This is used to identify the element in client-side javascript. See [Accessing widgets from javascript](uis.md#uitags) for more information on how and where to use them.
## Position Properties|
 



|Property|Description|
|--|--|
|Bottom|The position of the ui element relative to the bottom-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Height|The height of the ui element See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned and sized.|
|Left|The position of the ui element relative to the left-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Right|The position of the ui element relative to the right-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Top|The position of the ui element relative to the top-edge of its container. See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned.|
|Width|The width of the ui element See [Positioning and Placement of widgets](uis.md#uipositioning) for more information on how widgets are positioned and sized.
<a name='html-widget'></a>|
 

# Html Block
This is a generic container for arbitrary html.
Html in here can make use of [iviva Expression](ice.md#ice) syntax to formulate its content.

{% hint type="warning" %}
    This ui element has various security implications. It may be deprecated in the future. {% endhint %}

##  Properties



|Property|Description|
|--|--|
|Html|The actual html content to put in. This can make use of [iviva Expression](ice.md#ice) syntax.
## Appearance Properties|
 



|Property|Description|
|--|--|
|Visible|Controls whether the ui element is actually visible on the screen. If this is set to false, then the ui element is never rendered to the screen. This is property is useful only if you want to permanently hide a ui element (maybe beacuse you temporarily don't want to show it to anyone). If you want to control the visibility of a ui element based on some logic, use the VisibilityExpression property.|
|Visibility Expression|You can specify an [iviva Expression](ice.md#ice) expression here which should evaluate to true if you want the ui element to be shown. It should evaluate to false if the ui element should be hidden.
## General Properties|
 



|Property|Description|
|--|--|
|Auto Update|This property is currently not used.|
|id|An identifier for this ui element|
|tag|The tag is an identifier you can associate with the widget. This is used to identify the element in client-side javascript. See [Accessing widgets from javascript](uis.md#uitags) for more information on how and where to use them.
## Position Properties|
 

