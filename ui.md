


<a name='uis'></a>

# Building User Interfaces
Lucy comes with User Interface Composer, allowing you to design user interfaces to present to users.
These interfaces can be supported in the backend by models as well as iviva applications and services.

<a name='uibundles'></a>

## UI Bundles
All the user interfaces you define go into *UI Bundles*.
A UI Bundle is a collection of related interfaces that are packaged up together.
In the [UI Composer](uicomposer) you can work with one bundle at a time and edit all the screens in that bundle together.

For example, if you had a dashboard widget to show a list of recent incidents, a separate screen to view incidents and a popup dialog to close an incident directly from the dashboard, those three screens would go together as a single bundle. You can easily reference and link to other views within the same bundle.

These UI Bundles are also typically linked to a model.

Each model can be linked to a single ui bundle (typically having the same name as the model).
Models are linked to bundles from the [Model Designer](model-designer).
See [linkuimodel](linkuimodel) for more information on this.

{% hint type="note" %}
    Its only possible to link a model with a new UI bundle. You cannot link a model with an existing UI bundle. And a UI Bundle cannot be linked with multiple models. {% endhint %}

### Why do we need to link models to UI Bundles?
This is required if we want to override some of the model's dynamically generated user interfaces with custom ones that are defined in a bundle.
It's only possible to create override screens from the bundle that is linked to the model.

It's also required if the model needs to query any data sources using the |calldatasource| block.

It's only possible to query data sources that are defined in UI Bundles linked to models.

See [configdynuis](configdynuis) for more information on overriding the model's default screens.

## Accessing and Editing UI Bundles
UI Bundles can be accessed directly by going to the Lucy dashboard, clicking the image:: images/gear.png icon and then selecting 'View All User Interfaces'

From a model, you can directly go to its linked UI Bundle by going to the **UI** tab in the [Model Designer](model-designer) and following the link to view the user interfaces for that model.

<a name='uicontainers'></a>

## Types of User Interfaces
All user interfaces that can be designed in Lucy are web-based. They are responsive and render on desktops, tablets and mobile devices.
There are several types of *UI Containers* available - these are the starting point for designing your interface.
All your UI elements will go into these containers.

The available containers are:

- Simple Page - Use this to create simple screens that display and capture data
- Weblets - Use this to design dashboard weblets that can be either added to each user's main iviva dashboard or for use in dynamic dashboards.
- Tab Injection - Use this to design a tab that can be inserted in an existing iviva screen
- Dialog - Use this to design a popup dialog that can be invoked from somewhere
- Quick Info - Use this to design a  quick-information bubble that hovers above the page

<a name='commoncontainerprops'></a>

### Common Properties
All ui containers have several common properties. These can be set by clicking on that ui container in the [Bundle Explorer](bundleexplorer).

.. list-table::
    :header-rows: 1

    * - Name
      - Description
    * - ID
      - A unique identifier for this UI. This must be unique within the current bundle and is used to identify this particular UI.
    * - Name
      - A more descriptive name to give to the screen.
    * - Description
      - A description of what the screen represents. Currently used only for weblets - this description will appear in the weblet browser.
    * - SetupScript
      - Any [javascript](clientscript) to be run when the screen loads
    * - Permissions
      - The [permissions](uipermissions) associated with this is screen.


## Types of UI Elements
There are many UI elements that can be placed inside containers.
Please see the [widgetreference](widgetreference) section for more information.

## Designing the User Interface
You start defining a user interface by picking one of the containers and adding it to the bundle.

Click on one of the 'Add' links at the top of the Bundle Explorer to add a container to your bundle.

Once this is done, you can drag [fields](widgetreference) from the toolbox into the container to add a field to your user interface.

Depending on the field and container, you can drag around the field to place it where you want. In some containers, the layout is automatic an the field will go into a fixed position. See [uipositioning](uipositioning) for more information.

The next step is to bind data to your field.

## Using Data Sources
Data Sources are the central mechanism for gathering data to bind into a user interface.
You can design data sources to select the attributes you need, filter out data, group and sort them.

<a name='pageinputs'></a>

## Using inputs and parameters
Input parameters are important to the flow of UI screens and data within them.
This section explains how input parameters flow from the user to the screen and then down to the data sources.

Every [UI Container](uicontainers) accepts input parameters. These are known as **Page Inputs** and are specified by clicking on the container in the [Bundle Explorer](bundleexplorer) of the [UI Composer](uicomposer).
What you specify are the *expected* inputs to the page.

{% hint type="note" %}
    It is possible that the all of those inputs may not be specified at any given time or that extra inputs not specified there may be passed to the page. {% endhint %}

### How do you pass inputs to a page?
It depends on the UI Container itself.
Simple Pages and Injected Tabs read their inputs from the url query string.
For dialogs and quick info bubbles, the inputs must be specified by the screen that is invoking the dialog or bubble.
In the case of weblets, page inputs could come from either the query string of the page that the weblet is in, or it could come from the |addweblet| block which added the weblet, or from [Metadata Explorer](mde).

### How do you use page inputs?
Typically, page inputs are used in the [datasources](datasources) that the screen refers to. If the datasource has any [parameters](datasourceparameters) with names matching any of the page inputs, those parameters will get filled by the corresponding page inputs.

The one exception is datasources bound to a [celllist-widget](celllist-widget).
For these, the parameters to the datasource come from the values specified in the datasource section of the ui element.

Page Inputs can also be passed to [uiactions](uiactions) to be used as parameters to any action invoked by the user.

In addition, you may choose to use the page input parameters directly in the screens to populate labels or the visibility of certain sections.
The page's parameters can be accessed via [iviva Expression](ice) using the syntax: code/{param.pageinputname}.

For example, if you want to pass a page input called code/isactive and have it control the visibility of a [action-widget](action-widget), set that ui element VisibilityExpression property to code/#{param.isactive?}

{% hint type="warning" %}
    Showing or hiding elements based on page inputs is not secure!
    Page inputs can easily be modified by the user and spoofed.
    See [uipermissions](uipermissions) for information on how to restrict access to screens. {% endhint %}

<a name='databinding'></a>

## Binding Data
Once you have your ui elements setup, you can start binding data to it.

### Interactively binding data
You can drag fields from the [Data Source Explorer](datasourceexplorer) on the left on top of a ui element in order to bind that field to that widget. How the data is actually bound depends on the actual ui element. In some cases, data may be bound to the **Value** field of the ui element. In some cases, it may be the **Object Key** field or the **Text Field**.

When you drag a field over a ui element you will get feedback on whether or not that item can be bound to that widget.

{% hint type="note" %}
    Many fields can be dragged into an empty area of a UI Container and have it automatically create a relevant ui element and bind data to it in one shot.
    For example, dragging in a text field into an empty area creates a [label-widget](label-widget). Dragging in a object key creates an [objectlink-widget](objectlink-widget). {% endhint %}

{% hint type="note" %}
    When you drag an item into the content area of a [celllist-widget](celllist-widget) or a [repeater-widget](repeater-widget) then the data source that the field came from will get automatically bound as the datasource of that ui element.
    However you have to be careful to make sure you only drag in fields from the same data source, as these ui elements can only be bound to a single source. {% endhint %}

<a name='manualbinding'></a>

### Manually binding data
You can manually bind data to properties of a ui element by specifying an [iviva Expression](ice).
You can access fields in data sources by using the prefix code/#{services.datasourcename.field}

If you are binding data inside a [list](uilists) ui element, then use code/#{row.field} to access a specific field in each row of the [result set](dt-results).
The actual datasource to use will be bound separately for those ui elements.

{% hint type="note" %}
    You can drag fields from the [Data Source Explorer](datasourceexplorer) into Parameter Value entry fields in the action list property editor to automatically create a relevant [iviva Expression](ice) binding. Properties that support direct binding from the [Data Source Explorer](datasourceexplorer) will turn green when you drag a field over them. {% endhint %}


<a name='uilists'></a>

## Working with lists of items
A common UI metaphor is to display a list of items, with each item in the list being represented by a single result from a data source.

There are two ui elements available for doing this:

* [repeater-widget](repeater-widget)
* [celllist-widget](celllist-widget)

Both ui elements are setup in similar ways but differ in how they work at runtime.

[celllist-widget](celllist-widget) ui elements are designed to show a large volume of items (like search results) by showing only a few at a time and allowing the user to scroll down to view more details. As the user scrolls, the [data source](datasources) is requeried for more items. This is a highly effecient way of showing many items.
These ui elements also allow the parameters to the datasource to dynamically change.
[Data Source Parameters](datasourceparameters)  can be bound to other ui elements such that whenever those ui elements change their value, the [celllist-widget](celllist-widget) will refresh itself with new data based on the new parameters passed to the data source.

{% hint type="note" %}
    To make a datasource work with a [celllist-widget](celllist-widget) it must support incrementally returning data via a mechanism called pagination.
    See the section [pagination](pagination) for more information on how this works. {% endhint %}

[repeater-widget](repeater-widget) ui elements work by loading all data at once when the screen loads and showing it to the user. Use this when the number of items are small and you need to be able to see all the items at the same time.
The height of the [repeater-widget](repeater-widget) will vary based on the number of items it is showing.

To bind data to a list ui element, specify the datasource property of the ui element.

### Determining how each item in the list should look
To design how each item in the results should look, drag ui elements into the content area of the [celllist-widget](celllist-widget) or [repeater-widget](repeater-widget)

<figure><img src=' images/uilists.png'></figure>

Items in the content area get repeated for each row in the [result set](dt-results).
To bind data to these items use the code/row variable in your [iviva Expression](ice).

For example, if you specify code/#{row.Name}  as the Text property of a label in the content area, then for every row in the result, the code/Name  field will be bound to that label.

{% hint type="note" %}
    If you bind data by dragging items from the [Data Source Explorer](datasourceexplorer) they will automatically use the code/row variable if they are bound inside the content area of a list ui element. {% endhint %}


<a name='pagination'></a>

### Pagination in data sources
For data sources to work with [celllist-widget](celllist-widget) ui elements, they must support pagination.
By default, all datasources you define in the Data Source Designer support pagination.
However, if your data source is a model action, then you need to take extra steps to support pagination.

To support pagination, your action must accept the following inputs:

* **last** - The last value returned in the previous result. The action should use this value to seek ahead to the next set of results
* **max** - The maximum number of results it should return in one shot. If less results are returned, this indicates the end of the full result set.

The action's result must be a [result set](dt-results) and it must include one field in all results called code/__rowid__.
This field is a unique identifier for each result and should be increasing in value as you go down the result set.

(ie, a result later on cannot have a code/__rowid__ less than any of the previous results)


## Hooking up to models

<a name='uiactions'></a>

## User Interface Actions
Certain ui elements can react to user interactions (currently only *click* interactions are supported) and execute a sequence of UI actions in response to the click.
These actions may call a [model action](actions) to save data, may call an iviva service, navigate to a different screen, etc...

Multiple actions can be lined up in a sequence and they will execute one after another. In case any of the actions return an error, the full sequence will be aborted.

{% hint type="note" %}
    Certain actions are asynchronous (like executing a model action or an iviva service). Action Sequences are aware of this  and will line up the next action in the sequence such that it will only execute after the current one *completes*, not immediately after the current one fires. {% endhint %}

### Using the action editor
The action editor can be accessed from the property panel in the [UI Composer](uicomposer).
It is available for ui elements that support invoking actions (currently, [icon-widget](icon-widget) and [action-widget](action-widget))

<figure><img src=' images/actioneditor.png'></figure>


Multiple actions can be added. The configuration for each action will defer based on the type of the action.

<a name='axnparamconfig'></a>

### Configuring Parameters
Several of the action types take parameters as inputs.
You can map these parameters to page inputs, ui element values or hard-coded text.
When configuring a parameter, you can specify the following:

* **Parameter Name**  This is the name of the parameter to be passed to the action. Depending on the action, parameters can be added/removed or in some cases, they may be fixed, in which case you will not be able to edit the name of it.

* **Parameter Type**  This determines from where the parameter should obtain its value at execution time. The following parameter types are available
    * Field - Specify a ui element to take the parameter value from. In most cases, the *Value* property of the ui element will be used. In the case of a text entry ui element, the *Text* property will be used. The field selection list shows the ids of the available fields.

    * Page Input - Specify one of the page inputs to be passed as a parameter.

    * Value - specify a hard-coded value. You can also specify a [iviva Expression](ice) here.


The following action types are available:

### Execute iViva Service
This executes an iviva application service in the background. The next action is executed only upon successful completion of the current one.
You need to specify the service to call and any [parameters](axnparamconfig) to pass to it.
In the case of an error, an alert will be shown with the error message.


<a name='showqiaxn'></a>

### Show QuickInfo
Show a quick-info bubble near the ui element that was clicked on.
You need to pick a quickinfo from the current UI bundle and specify any page input [parameters](axnparamconfig) that the selected quickinfo requires.


### Query DataSource
Query a [data source](datasources) in the current bundle and return the result of it.
You can specify [parameters](axnparamconfig) to the data source.

Querying a datasource on an action is not very useful unless you plan on using it with [javascript](clientscript) later on.


### Navigate to Url
Specify a url to navigate to.
This url can be relative or absolute.
You can also use [iviva Expression](ice) here including parameters like code/baseurl to get the base url of the current iviva installation.

{% hint type="note" %}
    If you want to navigate to a page within iviva, your url should be of the from: code/#{baseurl}/Apps/AppName/viewname {% endhint %}


### Notify
Flash a notification message to the user briefly, for a few seconds.


<a name='axnmde'></a>

### Show Metadata Explorer
Show [Metadata Explorer](mde) and focus on a specific object.
You need to specify the object id, object key and object type as [parameters](axnparamconfig).


<a name='showdialogaxn'></a>

### Show Dialog
Similar to the quick-info action, invoke a dialog defined in the current bundle and show it in the center of the screen.
You need to pick a dialog from the current UI bundle and specify any page input [parameters](axnparamconfig) that the selected dialog requires.

Any actions after this action will be executed only if the [closedialogaxn](closedialogaxn) action is called within the dialog somewhere.
So if someone dismisses the dialog without invoking any action n it that calls [closedialogaxn](closedialogaxn), the rest of the actions in this list will not run.


### Navigate to UI
Navigate to a page defined in this UI bundle.
Specify any page inputs that the page requires.


### Model Action
Execute a Lucy model [action](actions).
Select a model, then select an action to execute.
When an action is selected, the required inputs will be listed and need to specified as [parameters](axnparamconfig).

If the action is being executed on an instance of a model, then a special parameter called code/Instance.Key will be in the list of parameters. This parameter represents the key of the instance that this action needs to execute in.

{% hint type="note" %}
    All actions are selectable here, not just the ones marked as public. {% endhint %}


### Custom Model Action
Similar to *Model Action*. In this case, you can explicitly specify an arbitrary model name, action and list of parameters.
Useful when setting up a UI for a model/action that has not yet been defined or is not yet available.


### Javascript
Execute arbitrary client-side javascript.
You can add multiple [parameters](axnparamconfig) to be passed to the javascript.
These parameters can be accessed in a javascript object called code/args.
To abort execution of the action list and any items after the current one, throw an exception from javascript.


    var param1 = args.parameter1;
    if (!param1) throw 'Parameter 1 was not specified';

{% hint type="seealso" %}
    [clientscript](clientscript) {% endhint %}

<a name='closedialogaxn'></a>

### Close Current Dialog
This action is only useful when being run within a dialog UI.
This closes the current dialog and triggers the caller to execute the rest of its action list.


### Reload Current Page
Exactly what it says :)


### Instance Model Action
These are not the droids you are looking for. Move along, move along.
(This action is deprecated)

<a name='uipositioning'></a>

## Positioning and Placement of ui elements
How ui elements are placed and sized in an interface depends on the ui element as well as the container that it is placed in.

Most containers have a **fixed layout** and so, adding a ui element to it will make that ui element automatically take up a known position and space in the container.
Other containers have a **free layout** in which ui elements can be freely moved around and sized independently of any other.


<a name='uifixedlayout'></a>

### Fixed Layouts
In fixed-layout containers, the ui elements will automatically occupy a given position and space within the container. The position of the widget can be changed by dragging them up/down (or left/right if the container stacks items horizontally).

There are two types of fixed layouts:

* Vertical Layouts - This is the most common type of layout. UI Elements that are added to this container go to the bottom of the container below the previous last ui element. The order of ui elements can be changed by dragging them up or down. The width of the ui elements cannot be changed - they occupy the full space provided by the container.
The height of the ui element can be adjusted if the individual ui element field allows for it.

* Horiontal Layouts - Currently only the [fieldline-widget](fieldline-widget) supports horizontal layouts. In this case, widgets get added to the right of the previous one. You can drag them left/right to re-order them. They take up the full height available to it, but the width of ui elements can be adjusted.


<a name='uifreelayout'></a>

### Free Layouts
In free layouts, ui elements can be placed anywhere in the container, can be dragged around to any position and can be sized by dragging the corner handles of the ui element.

### Specifying positioning
Along with dragging ui elements around to position them, you can do more sophisticated and accurate positioning of ui elements using the spacing panel in the [UI Composer](uicomposer).

Here you can enter exact values for code/Left and code/Top properties of the ui element in order to state exactly how far from the left and top edges of the container the widget should be positioned.
You can also use the arrows to nudge them slightly, one way or the other.

<figure><img src=' images/sizing-panel.png'></figure>

### Anchoring items to the right or bottom
There are many times when you may want to anchor an item to the *right* edge of the screen or to the bottom of the screen instead of the default behaviour of anchoring them relative to the left/top.
This is useful in places like a [celllist-widget](celllist-widget) or a [repeater-widget](repeater-widget) where one item element (maybe a link or an icon) needs to be kept on the right edge of the screen, regardless of how big the screen is.

To anchor items to the right, you need to specify position values for the code/Right section in the spacing panel.
When you specify a value for the code/Right section, any value set in the code/Left section will automatically be removed and will be kept empty.

The value you specify for the code/Right section determines how much space should be present between the *right edge* of the ui element and the *right edge* of the container. The lower the value, the more closer to the right edge of the container, the widget will be placed.

It is not technically possible to specify both a left and right value. Only one of them can be used. If both happen to be specified, then priority is given to the code/Left value.
So you need to explicitly clear out the code/Left value in order to make use of right-anchoring.
The [UI Composer](uicomposer) will clear the value automatically when you set a value for the code/Right section.

{% hint type="warning" %}
    Whenever you explicitly drag around a ui element,the left and top values automatically get specified, which wipes out any bottom/right anchoring values you have set. {% endhint %}

{% hint type="note" %}
    The easiest way to right-anchor an element is to simply go to the code/Right section and use the arrows to nudge it. This will automatically set a value for the code/Right section an empty out the value in the code/Left section. {% endhint %}

{% hint type="note" %}
    When right-anchoring labels, remember to set the TextAlignment property as well to right-align the text. {% endhint %}


### Specifying Spacing
Widget spacing in free layouts can be specified by dragging around the corner handles when selecting the widget.
For more refined and precise spacing, use the code/Width and code/Height properties in the spacing panel to set specific values.

When setting values, the default is to use code/px. However, you can also set a width and height as a *percentage* by adding a code/% suffix to the value.

When specifying a width or height as a percentage, the ui element will take up space equal to that percentage of the container's space.

For example, if you specify a ui element take code/50% width, then it will occupy a width equal to half of the width of the container its in.

You can use the code/Stretch links to automatically set the width/height to code/100%


## Simple Pages
This container represents a simple stand-alone web page.
The screen will have the usual iviva chrome around it - app menu, toolbars etc... The screen is responsive and can be viewed on both desktop and mobile clients.
This container uses a [fixed layout](uifixedlayout).

This is the only type of UI screen which can be directly accessed via a url.

The url for the screen will be of the form:

```

    http://<ivivacloudurl>/Apps/Lucy/cv-<bundleid>-<pageid>

```


In addition to [commoncontainerprops](commoncontainerprops), pages can also have Page Inputs.
These page inputs are specified by query string parameters to the url of the page.

{% hint type="seealso" %}
    [pageinputs](pageinputs) {% endhint %}

Every page has a title seciton where you can enter a title for the page.
Just click in the title section and type to edit the title.
You can use [iviva Expression](ice) syntax in the title.

{% hint type="note" %}
    You can preview the pages by launching them in a new window.
    Click the **Preview** link in the property panel for the page (located near the bottom).
    Remember to save your UI Bundle first! {% endhint %}


<a name='weblets'></a>

## Weblets
Weblets are the small widgets that make up dashboards in iviva.
Weblets can be added to a user's home dashboard by using the weblet browser.
Weblets can also be added to a [dynamic dashboard](dyndashboards) by using an |addweblet| block or via the [Metadata Explorer](mde).

Weblets use a [free layout](uifreelayout) so ui elements can be arbitrarily placed in them.

They have two sections:

* **Body** - This is the main content area of the weblet
* **Options** - This is the slide-in panel that shows various options for the weblet. Place any filters or actions that are not highly used in here.

{% hint type="note" %}
    Weblets have a fixed height but can have a variable width depending on how the weblets are arranged. When positioning ui elements in your weblet, use percentage based dimensions and use left/right anchoring to get the spacing to look good regardless of the actual width of the weblet.
    See [uipositioning](uipositioning) for more information. {% endhint %}

{% hint type="note" %}
    Weblets that are designed to be used in a [dynamic dashboard](dyndashboards) often take a code/key parameter as input - representing the code/key of the instance that the dashboard is in.
    However, if your weblet is meant to be added via an |addweblet| block, then you can specify any page inputs you want. The |addweblet| block's pins will reflect the inputs that you specify. {% endhint %}

In addition to [commoncontainerprops](commoncontainerprops), weblets can also have Page Inputs.
These page inputs are specified either by the url of the page containing the weblet, or as an input to the |addweblet| block, or as the code/key parameter of the node in the [Metadata Explorer](mde).

They also have a **Publish** property which marks the weblet as published.
Once a weblet is published, it is available in the weblet browser and other places where weblets can be chosen. You can unpublish a weblet by unchecking the box. Once a weblet is in published state, its id cannot be changed.


<a name='tabinjections'></a>

## Tab Injections
This container represents a single tab that can be *injected* into the tab set of another page.
This is useful for adding new tabs to existing pages in iviva.

This container uses a [fixed layout](uifixedlayout).

In addition to [commoncontainerprops](commoncontainerprops), tabs can also have Page Inputs.
These will be read from the query string of the page that the tab is being injected into.


### Specifying where the tab should be shown
Under the properties section of the tab container,you can choose which view in which app to inject the tab into (obviously it has to be a view that has tabs in it).

The view has to support tab injections - most of them do.
You can get the view name and app name for  a page from the url. The url is of the form http://server/Apps/AppName/viewname?….

You can also specify a visiblity expression and a sidebarid.
The visibility expression is an [iviva Expression](ice) that you can use to evaluate whether to show the tab or not.
It will typically be something like code/#{services.ModelDetails.Key?}
(Which means, show the page if ‘Key’ attribute of the datasource named ‘ModelDetails’  has a valid value)

One way of using tabs may be to show one tab when no extension OI model exists (allowing the user to enter details to create the instance) and another when an extension model exists.
So the ‘create new’ tab would have a visibility expression like code/#{!services.ModelDetails.Key?} - meaning it should show only if ‘Key’ doesn’t have a valid value.
And the other tab would have a visibility expression of code/#{services.ModelDetails.Key?}

The sidebar id can be used to show the existing screen’s common sidebar as part of the tab.
You will need obtain this information from the application developer.

Once your tab is ready, to allow it to actually be injected into the page, you need to publish it by checking off the code/Publish option in the properties panel.

{% hint type="seealso" %}
    [ivivaintegration](ivivaintegration) {% endhint %}

## Quick Info Bubbles
Quick Info Bubbles are small bubbles of information that appear above an object when you click on it. They are used to provide extra information that may not be possible to put on the page itself. They can also be used for quick inputs and feedback. They disappear if the user clicks anywhere outside the bubble.

Every model instance, by default, has a dynamically generated quick-info bubble associated with it. It's possible to override the default one with a custom one that you design here.

Quick Info Bubbles use a [free layout](uifreelayout) so ui elements can be arbitrarily placed in them.
They have two sections:

* **Header** - The title section of the bubble - this contains the name of the item being viewed as a link that can navigate to that item's details page. You would typically use an [objectlink-widget](objectlink-widget) here.

* **Body** - The main content area of the quick info bubble. Place your content here.

{% hint type="note" %}
        You can drag the right edge of the bubble to make it wider. {% endhint %}

In addition to [commoncontainerprops](commoncontainerprops), quick info bubbles can also have Page Inputs.
Typically, the bubble would take a code/key parameter as input, indicating what object the bubble is going to render information for.

### Invoking Quick Info Bubbles
Quick Info bubbles are invoked by calling the [showqiaxn](showqiaxn) action.
They can only be called from other screens in the same UI Bundle.

## Dialogs
Dialogs are used to popup small modal screens on top of the current screen.
They can be dismissed by clicking the 'X' on the top right or by clicking outside the dialog.
Use dialogs to popup data entry and user feedback interfaces without having to navigate away from the current page.

Use the [closedialogaxn](closedialogaxn) action to close a dialog through an action.


Dialogs  use a [fixed layout](uifixedlayout)

Every dialog has a title seciton where you can enter a title for the dialog.
Just click in the title section and type to edit the title.
You can use [iviva Expression](ice) syntax in the title.


In addition to [commoncontainerprops](commoncontainerprops),
dialogs have two additional properties:

* **Color Scheme** - specify a color scheme to use for the background of the dialog box.

* **Page Width** - specify the width of the dialog in pixels. (Leave this empty to use a good default)

### Invoking Dialogs
Dialogs are invoked by calling the [showdialogaxn](showdialogaxn) action.
They can only be called from other screens in the same UI Bundle.


<a name='clientscript'></a>

## Client-Side Javascript in User Interfaces
.. warning::
    This is an advanced area. Implementations involving javascript have security and compatibility concerns. Use this judiciously.

Some times, if you need more sophisticated user interactions or rendering in your screens, you may choose to use javascript.
Javascript can either be invoked from the Setup Script property of the UI container, or from a Script action.

Javascript you write is fully executed in the context of the browser the user is running in so you will have to take care to ensure that your scripts work on all major modern desktop and mobile browsers.

The following javascript libraries are available to every page to make use of:

* jQuery 1.7
* underscore.js 1.3.1 - Useful utility functions
* date.js 1.0 Alpha-1 - Date parsing and manipulation
* v3 - This is the iviva javascript library. Please consult the iviva documentation for information on how to use it beyond what is discussed here.

<a name='uitags'></a>

### Accessing ui elements from javascript
You do not have access to the actual code/id of the DOM elements that ui elements render into. Instead, you need to use the code/tag property of the ui element to identify it.
Every ui element has a code/tag property which can be set to any identifier you want.

Once this is set, you can use the code/ServiceDesk.getFieldIDsByTag(tagname) function to retrieve all the DOM elements that match the tag you have given (ideally there should be only one result)

A Quick Example: Setup a text field with a tag called 'userid' and a checkbox called 'enable' and enter the following into the SetupScript property of the page.

```

    var checkboxID = ServiceDesk.getFieldIDsByTag('enabled')[0];
    var textboxID = ServiceDesk.getFieldIDsByTag('userid')[0];

```

    var cb = $(document.getElementById(checkboxID));
    var tb = $(document.getElementById(textboxID));

    cb.bind('change',function(evnt) {
    	if (cb.is(':checked')) {
    		tb.removeAttr('disabled');
    	} else {
####     		tb.attr('disabled','disabled');
    });


This will cause the textbox to get enabled/disabled as you check/uncheck the checkbox.


<a name='uipermissions'></a>

## Applying Permissions to User Interfaces
You can restrict access to user interfaces by setting permissions.
Each UI Container has a **Permissions** property that can be set.
If that property evaluates to code/false then the page will not be accessible.

You can use an [iviva Expression](ice) to specify rules that should evaluate to true or false.

You can refer to [app roles](approles) that are defined in your models by the syntax: code/#{authrole.Lucy.models.modelname.rolename}

For example, if you have a model called code/StaffExtension and have defined two roles code/canupdate and code/candelete and want only users who have any of these roles to be able to access the page, you can specify an [iviva Expression](ice) like:

```

    #{authrole.Lucy.models.StaffExtension.canupdate? or authrole.Lucy.models.StaffExtension.candelete?}

```

Your expressions can incorporate page inputs and data sources and can be arbitrarily complex.

{% hint type="seealso" %}
    [permissions](permissions) {% endhint %}