


<a name='uicomposer'></a>

# UI Composer Reference

    The UI Composer can be accessed by going to the Lucy app and then clicking on the image:: images/gear.png icon and selecting **Build a user interface** from the menu.
    Alternatively, you can search for an existing UI Bundle by clicking on **View all interfaces** and click it to open it up in.


The UI Composer is where you design and build your custom user interfaces for Lucy.


<figure><img src=' images/uicomposer-annotated.png'></figure>


The UI Composer consists of the following parts:

1. [Bundle Explorer](uicomposer.md#bundleexplorer)
2. [DataSource Explorer](uicomposer.md#datasourceexplorer)
3. [Design Area](uicomposer.md#designsurface)
4. [Datasource Designer](uicomposer.md#datasourcetab)
5. [Toolbox](uicomposer.md#toolbox)
6. [Property Panel](uicomposer.md#propertywin)

<a name='bundleexplorer'></a>

## Bundle Explorer
The bundle explorer shows you all your [UI Bundles](uibundles).
You can click the image:: images/attradd.png icon to add a new screen to the bundle.
You can expand each item to see its sub components and ui elements. Clicking on any of them will select that widget or screen and show its properties in the property panel.

See [Types of User Interfaces](uis.md#uicontainers) for information on the types of screens you can create.

<a name='datasourceexplorer'></a>

## DataSource Explorer
The data source explorer shows you all the datasources that are accessible in this bundle.
This includes:

1. Data sources defined in the datasource designer.
2. Any actions in a [linked model](linkuimodel)
3. Any custom data sources that have been made available in the system.

Custom Data Sources are published by iviva applications and can be added to the bundle. Click the `Include a custom data source` link to select a custom data source and add it. Custom data sources are useful to provide access to data that cannot otherwise be extracted using the datasource designer or model actions.

You can expand each data source to see its fields. The fields can be dragged into the design surface to bind them to ui elements.

See [Binding Data](uis.md#databinding) for more information on how to bind datasource fields to ui elements.

{% hint type="note" %}
    Some datasources that represent model actions may not show any fields when expanding the source. You can still bind data to the fields using [iviva Expression](ice) syntax but interactive binding by drag and drop of those sources may not be possible. See [Manually binding data](uis.md#manualbinding) for information on how to do this. {% endhint %}

<a name='designsurface'></a>

## Design Area
This is the center area where you can see your user interface screens, edit them, place ui elements in them and edit their properties.

To add ui elements to container, drag the widget from the toolbox into the design area onto the place where you want to add it.
Depending on the type of screen the ui element is added to, it may get added at the bottom of a list of elements, or may get added somewhere in the middle.
You can always drag them element around to re-arrange it.

All screens are shown in one giant layout, one below each other.
Click on a screen in the bundle explorer to navigate straight to that screen.

UI Elements can be selected by clicking on them. You can move them around by dragging them and you can resize them by dragging any of the corner handles.

The property panel shows details about the selected ui element.

You can select multiple ui elements by holding `Shift` and clicking on items.

{% hint type="note" %}
    The property panel only shows items for the first selected ui element {% endhint %}

{% hint type="note" %}
    You can also `Shift+Click` on items in the bundle explorer to select them. {% endhint %}


<a name='datasourcetab'></a>

## Datasource Designer
The second tab in the UI Composer is where you design custom data sources.
See [Working with Data Sources](datasources.md#datasources) for a complete overview on how data sources work.

<a name='toolbox'></a>

## Toolbox
The toolbox contains a list of all available ui elements. To add a ui element to a screen, drag that item from the toolbox into the design area.

For a full list of available ui elements, see [wigetreference](wigetreference)

<a name='propertywin'></a>

## Property Panel
The property panel shows details about the currently selected object.
This could be a ui element or it could be an entire screen itself (you can select the screen by clicking it in the bundle explorer).
From here, you an edit the various properties of the item.
Properties are divided into tabs with different properties being shown in different tabs.

The four common tas are:

* image::  images/uic-general-tab.png - General properties like the element `id` and `tag`
* image::  images/uic-spacing-tab.png - The spacing panel where dimension and position properties are set. See [Positioning and Placement of ui elements](uis.md#uipositioning) for a completely boring but nevertheless thorough walk-through of how positioning works.
* image::  images/uic-appearance-tab.png - Properties related to the appearance of the ui element. Includes text display properties.
* image::  images/uic-actions-tab.png - The actions editor for ui elements that support invoking actions. See [User Interface Actions](uis.md#uiactions) for more information about invoking actions in UI screens.

From the property panel, you can also copy and paste selected ui elements.

Click the image:: images/trash.png icon to delete the selected widget.