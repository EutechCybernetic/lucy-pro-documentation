

<a name='dynuis'></a>

# Dynamic User Interfaces
Lucy has the capability to dynamically assemble user interfaces for common tasks related to your model.

User interfaces can be generated for

1. searching instances of your model
2. viewing details of a specific instance
3. creating a new instance of a model
4. viewing a quick-information 'bubble' showing a preview of information about an instance.

Each of these interfaces can also be optionally overriden with a custom user interface that you can design and build.

<a name='configdynuis'></a>

## Configuring Dynamic User Interfaces
You have a certain amount of control over what the dynamically generated interfaces show.
You can control these settings from the **UI** tab in the [Model Designer](model-designer).

In that tab, there are sections for the various types of user interfaces.
Check the checkbox near the user interface to indicate that you want the interface to be generated by Lucy automatically.
Uncheck that box to select your own user interface instead.

{% hint type="note" %}
    In order to select your own user interface, you need to [link your model](linkuimodel) with a UI Bundle. {% endhint %}

If you choose to use a dynamically generated user interface, there will be further settings to let you select what attributes to show in the user interface and which [app roles](approles) are required to access it.


## Accessing Common User Interfaces

### Instance Search Page
The search page for your instance can be accessed by either

* Going to the Lucy dashboard, click the image:: images/gear.png icon, then choose `Models`
    * Locating your model, and then clicking the **Search** link next to it
* Directing from the url: `http://<ivivacloudurl>/Apps/Lucy/Models/<yourmodel>/search`

If you have not overriden your search page with a custom screen, the dynamically generated search page is shown.

#### Dynamically Generated Search Pages
The dynamically generated search page works like any standard iviva search page.
There is a textbox on the top to let you do a text search across all instances of the model. On the right are filters to filter the search results.
In the middle is the actual search results.

From the **UI** tab in the [Model Designer](model-designer), you can select which attributes to be shown in the search results and which attributes to use as filters.

Any text attributes that you choose to use as filters will be used for searching when typing text into the text box at the top of the page.

Any object and [timestamp](datetimes) attributes that you choose to use as filters will appear in the right side of the search page in the filters section.

If you choose to include a [timestamp](datetimes) filter, two filter controls will be shown in the search page - one to choose the start date and one to choose the end date. Instances that have an attribute value falling in between those two will be shown.

By default, every search page has one filter: *Active Status* - which allows you to show only active instances or all instances (including inactive ones).


You can also choose which attributes to show in the actual search results for each instance.
Search results always have at least three items:

1. Active Status Indicator - This is an indicator whether the instance is active or not
2. Instance Name - This is the name of the instance. This will also act as a link to navigate to the instance details page.
3. A image:: images/quickinfo.png icon on the right side - clicking it will show a quick-info bubble about that particular instance.

Any attributes you select to show in search results will show up inbetween the Name field and the quick info icon on the right.

{% hint type="note" %}
    Try to limit the number of attributes you show in search results - both for performance reasons and because of space constraints.
    You can always view more attributes in the quick-info bubble. {% endhint %}


<a name='instancedetailsui'></a>

### Instance Details Page
The details page for an instance shows information about that particular instance.
This includes a list of attributes of the instance, as well as any dynamic dashboard that is associated with that instance.

Instances can be accessed by clicking a link in a instance search page.
It can also be accessed by going to:

```
        http://<ivivacloudurl>/Apps/Lucy/Models/<modelname>/view?key=<instancekey>```

{% hint type="note" %}
    It is currently not possible to override the details page with your own. {% endhint %}


The instance details page has two tabs:

* Dashboard
* Details

The Dashboard tab will show any dashboard associated with this instance.
See the section on [Dynamic Dashboards](dynamicdashboards.md#dyndashboards) for how to create and use dynamic dashboards.

{% hint type="note" %}
    Its possible that your instance does not have any dashboard associated with it at all. In this case, the dashboard tab will be empty and the screen will default to showing the Details tab. {% endhint %}

The details tab contains all the important attributes of your instance.
You can edit them from this screen by clicking the image:: images/pencil.png icon at the top right corner of each attribute.


Only attributes you have chosen to show will be displayed here. See [Configuring Dynamic User Interfaces](dynamicuis.md#configdynuis) for more information on how to configure what is shown.

{% hint style="info" %}

    If you wish to see all attributes of the model (for testing or diagnostic purposes) beyond what you have configured to be shown, you can always go to: `http://<ivivacloudurl>/Apps/Lucy/inspectinstance?key=<instancekey>`

{% endhint %}

    That screen will show you all attributes of a given instance.

From the instance details screen you can choose to deactivate the current instance. Click the **Deactivate** link in the sidebar to cause this instance to get deactivated.

{% hint type="seealso" %}
    [Removing |instances|](instances.md#deactivateinstance) for more information. {% endhint %}

<a name='instancecreationdialog'></a>

### Instance Creation Dialog
Another interface that you get for free when you define a model is a dialog screen to create a new instance of that model.
Once you have created the instance, you will get redirected ot the instance details screen.
This screen can be accessed either

    1. This can be done by clicking the *Create New Instance* link in the side bar of the model designer.
    2. If you define an extension attribute in your model, then from that extension's interface, you can click the |mapextension| icon and invoke the dialog.

When the dialog is invoked from an extension attribute screen, the relevant extension attribute's value will be auto filled.

From the **UI** tab in the [Model Designer](model-designer) you can select which attributes will be captured in the dialog.
If you have marked an attribute as `Required` in the [Attribute Editor](modeldesigner.md#attributeeditor) then the dialog will validate that the attribute's field is filled when creating an instance. See [Configuring Dynamic User Interfaces](dynamicuis.md#configdynuis) for more information on configuring the creation dialog.


#### Overriding the creation dialog
You can override the default creation dialog by defining your own dialog screen in the [UI Composer Reference](uicomposer.md#uicomposer). In the **UI** tab of the [Model Designer](model-designer) uncheck the option to auto-generate a creation dialog and instead, pick the dialog you have defined from the list.

{% hint type="note" %}
    You need to create a dialog screen in the UI Bundle. Only dialog screens will be shown in the list of views to override with. {% endhint %}

See [Configuring Dynamic User Interfaces](dynamicuis.md#configdynuis) for more information.

### Quick Information Bubble
The quick-information bubble shows a small bubble of information about your instance along with a link to go to the instance details screen. This bubble is auto-generated and, just like the other auto-generated screens, you can choose what attributes you wish to show.

This bubble is available in the search page by clicking the  image:: images/quickinfo.png icon. It is also shown in the metadata explorer when you click a node that represents an instance of this model.

You can override the default bubble with a custom one - that shows information in any way you want.

To create a custom quick info bubble:
* Add a new quickinfo UI to your UI Bundle.
* Add a page input called `key`. This parameter represents the key of the instance that is being shown
* Use the `key` parameter to pull data and bind it to fields in the UI
* Give a unique id for your bubble and save it
* In the **UI** tab of the [Model Designer](model-designer), uncheck the *Auto Generate Quick Info* option and select the quickinfo view you created from the list of views to override with.

{% hint type="note" %}
    The `Required` flag that you set for attributes is considered only if the dynamically generated dialog screen is used. If you choose to override the dialog with your own, you will have to perform your own validation - presumably in whatever action sequence you trigger from your custom dialog. {% endhint %}


.. toctree::
   :maxdepth: 1

   dynamicdashboards