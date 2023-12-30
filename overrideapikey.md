

[overrideapikey:](overrideapikey:)

================
# Override API Key

This feature allows you to provide a master API Key for your Lucy action or events, which would be preferred over the one passed. This is useful in the following scenarios,

1. Lucy events generally don't have any API Keys in context. In such case, calling any iviva service that requires one could fail. Here, providing an API Key override would solve that issuee.
2. Lucy actions can be published as API's for external access as mentioned in [Publishing APIs](_publishapi). You could choose not to have any authentication for this API, but might be calling an iviva service that requires one. Here, providing an API Key override would solve that issue.

Let's look at how to configure and use API Key overrides for,

1. `Lucy Actions`_
2. `Lucy Events`_

# Lucy Actions

*First step* is to enable the override,

1. Goto your lucy action in modeldesigner
2. Check *Can Override Credentials* option from the block's properties
3. Save your model

**Illustration**

<figure><img src=' images/override-apikey/action-block-override-apikey.png'></figure>

*Second step* is to create the override,

1. Click on image:: images/attrsettings.png in Lucy dashboard view and choose **Model Credential Overrides** under **Manage** section
2. Or, goto *<your_iviva_url>/Apps/Lucy/modelcredentialoverrides*. For example: http://testaccount.ivivacloud.com/Apps/Lucy/modelcredentialoverrides
3. Click on *Actions* tab
4. Search for you action by its *name* or locate the correct one from your list
5. Click on image:: images/pencil.png icon
6. In *Edit Action Credentials* dialog, provide a value for *Override Api Key* field and click on *Update*

{% hint style="info" %}

    To revert the override, simple uncheck *Can Override Credentials* and save your model. Or, set the override API Key to an empty string. In the second option, you need to reload your model by saving it in modeldesigner, restarting lucy or reloading lucy with the command **sdm broadcast config/reset 1**.

{% endhint %}

**Illustration**

<figure><img src=' images/override-apikey/model-credential-overrides-menu.png'></figure>

<figure><img src=' images/override-apikey/action-credential-overrides.png'></figure>

<figure><img src=' images/override-apikey/action-update-override-apikey.png'></figure>

# Lucy Events

*First step* is to enable the override,

1. Goto your lucy event in modeldesigner
2. Check *Can Override Credentials* option from the block's properties
3. Save your model

**Illustration**

<figure><img src=' images/override-apikey/event-block-override-apikey.png'></figure>

*Second step* is to create the override,

1. Click on image:: images/attrsettings.png in Lucy dashboard view and choose **Model Credential Overrides** under **Manage** section
2. Goto *<your_iviva_url>/Apps/Lucy/modelcredentialoverrides*. For example:  http://testaccount.ivivacloud.com/Apps/Lucy/modelcredentialoverrides
3. Click on *Events* tab
4. Search for you action by its *name* or locate the correct one from your list
5. Click on image:: images/pencil.png icon
6. In *Edit Event Credentials* dialog, provide a value for *Override Api Key* field and click on *Update*

{% hint style="info" %}

    To revert the override, simple uncheck *Can Override Credentials* and save your model. Or, set the override API Key to an empty string. In the second option, you need to reload your model by saving it in modeldesigner, restarting lucy or reloading lucy with the command **sdm broadcast config/reset 1**.

{% endhint %}

**Illustration**

<figure><img src=' images/override-apikey/model-credential-overrides-menu.png'></figure>

<figure><img src=' images/override-apikey/event-credential-overrides.png'></figure>

<figure><img src=' images/override-apikey/event-update-override-apikey.png'></figure>