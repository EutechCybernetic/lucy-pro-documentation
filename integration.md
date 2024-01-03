


<a name='ivivaintegration'></a>

# Integration with iviva
This section outlines how you can provide deeper integration between your Lucy models and iviva and extend iviva application functionality with the use of Lucy.

## Extension Models
The most common way of enhancing iviva applications with specific custom-tailored features, is to build an extension model.

If you need to enhance existing iviva objects by capturing more details, presenting different screens or adding custom logic, you can use Lucy to do this easily.

1. Define an extension model to capture any extra data you need
2. Decide how your extension model will get created
3. Listen for iviva application events and react to them
4. Build tabs that can be injected into existing iviva applications
5. Design weblets that are tailored to your new use-cases

<a name='extensionmodels'></a>

## Defining an Extension Model
An extension model is just like a normal Lucy model, except one of its attributes is marked as an *extension* of another object.

For example, if we want to enhance the *Staff* object in iviva to add more attributes to it, we can create an extension model called `StaffExtension`.
This will have an attribute that points to the iviva staff object (`Organization.OrgStaff`) and will be marked as an extension.
We will also add any other attributes that need to be captured about the staff.

To mark an attribute as an extension, go to the [Attribute Editor](attributeeditor), click on the image:: images/attrsettings.png icon next to the attribute and check-off the **Extension** checkbox.
Once this is done, this model will now be marked as an extension of the `Organization.OrgStaff` object.

When you visit the iviva Staff details screen, at the top right corner, you should see a image:: images/metadatamap.png icon. Click on it to bring up a list of any extensions that exist for this object.

{% hint type="note" %}
    Don't see the image:: images/metadatamap.png icon? Contact your application developer to get it added! It's a one-time task to enable support for extensions. {% endhint %}

That menu will show you any existing extension objects and will give you the option of creating one if one doesn't exist.

<figure><img src=' images/extension.png'></figure>

{% hint type="note" %}
    For a given extension model, only one instance of it can exist as an extension of another object. So if one already exists, the menu will show it to you. If one doesn't exist, you will be given the option to create one. {% endhint %}

When you click the option to create a new extension, that model's [Instance Creation Dialog](dynamicuis.md#instancecreationdialog) will be shown with the extension attribute's value auto-filled to the current object.

{% hint type="note" %}
    You can override the default creation dialog with your own. See [Configuring Dynamic User Interfaces](dynamicuis.md#configdynuis) for more information. {% endhint %}

After creating the instance, you will be redirected ot the instance's details page.

## Decide how your extension will get created
We just saw that one way of creating an extension is by using the image:: images/metadatamap.png icon at the top of each object screen.
Another method is to automatically create the instance whenever some event occurs.
You could automatically create a new StaffExtension instance when a staff is registered in the system, or you could have it created whenever the staff gets assigned to a department, etc...

To do this,
1. Locate the event you want to create  a new extension in response to
2. Add an event handler block to listen to that event and create a new instance.

### Locating the event
Most iviva application generated events are of the form:

```
    Application.Object:Action```

Virtually all of them emit a `Created` event and a `Modified` event. Both of  them pass the `ObjectKey` of the newly created/modifeid object as parameters.

For example, if we want to create our StaffExtension when a new staff gets registered, we need to trap the `Organization.OrgStaff:Created` event and handle it.

1. Locate that event in the [Model Designer](model-designer) event tab
2. drop the block into the design surface.
3. Set the mode of the [Event Start](eventstart-ref) block to *Trigger new Instance*
4. Read the `ObjectKey` parameter from the event and assign to your extension attribute

That's it!  Your StaffExtension instance will now get created whenever a new Staff is created in the system.

{% hint type="seealso" %}
    [Event Stream and Event Handling](events.md#eventhandling) {% endhint %}


To do this, listen to an event that gets emitted from the iviva application. Mark that event block as *Trigger new instance*.

{% hint type="note" %}
    The object you want to extend doesn't emit the required events you need? Contact the application developer and ask them to add it! {% endhint %}

## UI Integration

### Tabs
The easiest way to integrate into an iviva application screen is by tab injection.
Most iviva objects have screens arranged around tabs and have provisions for adding new tabs to them dynamically.

To inject a tab, you need to design a tab in the [UI Composer](uicomposer).
First create a new UI bundle for your model.
See [Linking your model to a user interface](customuis.md#linkuimodel) for more information on how to do this.

Then design your tab and set it up to be injected into the iviva screen.
See [Tab Injections](uis.md#tabinjections) for more information on how to inject a tab.

### Weblets
You may also want to provide dashboard weblets that act as the launchpad to your models. Weblets can be published and any interested user can add the weblet to their home screen. From these weblets, you can provide links into your specific screens and models.

See [Weblets](uis.md#weblets) for more information on designing weblets.