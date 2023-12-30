


[mde:](mde:)

# Metadata Explorer
The metadata explorer is a visualization tool in iviva to let you explore and visualize relationships between your objects and systems.

It focuses on a specific object and then lets you expand out and see related objects. When you click on each object, quick-info for that object is displayed as overlay on the left.

On the right, any related weblets will be shown for the node that is clicked on.

<figure><img src=' images/mde.png'></figure>

## Invoking the explorer
To invoke the metadata explorer for a specific object, click the image:: images/mdeicon.png in that object's details screen. This will also work for any Lucy model instance details screen.

The icon is also present in quick-info bubbles.
You can also manually invoke it from a custom ui using the [axnmde](axnmde) action.

The metadata explorer shows connections between objects automatically. If your model instance is connected to another object through an attribute, that connection will be shown.

When you define an attribute as an extension, then expanding the target object will show your extension instance as a related node.


## Setting up custom weblets
You can setup weblets to be shown when a node is clicked.
To configure this, go to the Lucy dashboard, click the image:: images/gear.png icon, then click the **Metadata Explorer Configuration** item.

In the configuration screen, select the object type you want to customize. This list will include all iviva objects as well as Lucy models.
After selecting one, go to the *Weblets* section below, click the image:: images/attradd.png icon,  and then choose a weblet from the list.
The list of weblets shows all published weblets that are available - both in iviva apps as well as weblets published in any [UI Bundle](uibundles).

When the weblet is displayed in the explorer after clicking a node, a code/key parameter is passed to the weblet which holds the object key of the node that was clicked on.

You can use this parameter in your weblet to show customized information for that particular node.