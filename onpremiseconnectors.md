


<a name='onpremiseconnectors'></a>

# On-Premise Connectors
On-Premise Connectors allow Lucy to securely communicate with building control systems, databases, files and other systems that are deployed on your premises.

Many connectors come bundled with Lucy. You can also develop your own connector using our SDK.

For Lucy running on the cloud to be able to communicate and exchange data with on-premise local systems, a *gateway* needs to be installed.

Each type of connector requires its own gateway. Gateways are currently available for Windows and run as Windows NT Services.

## Connector Types
Lucy comes bundled with connectors for various building control systems and databases.
All connectors expose functionality as separate blocks that are available in the [block panel](modeldesigner.md#blockpanel).

Some examples:

* BACnet - This connector lets you query and control devices that communicate via BACnet protocol.  The gateway for this connector needs to have network access to your BACnet interface. In your model you can use GetData and SetData blocks, and specify the point address parameters and the connector name.
* Modbus - This connector lets you query and control devices that communicate via Modbus protocol.  The gateway for this connector needs to have network access to your Modbus controller. In your model you can use GetData and SetData blocks, and specify the point address parameters and the connector name.
* OPC - This connector lets you query and control devices that communicate via OPC protocol.  The gateway for this connector needs to have network access to your OPC controller. In your model you can use GetData and SetData blocks, and specify the point address parameters and the connector name.
* Obex - This connector lets you query and control devices that communicate via Obex protocol.  This is often used to talk to a Niagara device. The gateway for this connector needs to have network access to your OPC controller. In your model you can use GetData and SetData blocks, and specify the point address parameters and the connector name.
* SqlServer - This connector lets you run queries on an Sql Server instance running on-premise.  The gateway for this connector will let you exchange data with Sql Server running in the local premise network. You can use the Query block to run parameterized queries.

You can see the full list of connectors by opening the image:: images/gear.png menu in the Lucy dashboard and select 'Connector Registry ' under 'On-Premise Connectors'.

{% hint type="warning" %}
    Do not edit the configuration of each connector type unless you are sure about what you are doing. Modifying it may cause the connector and blocks to stop working. {% endhint %}

## Using a connector
In the [block panel](modeldesigner.md#blockpanel) in the designer, you can see categories for each connector type that you have.
Open a category and view the available actions for that connector.
These actions may allow you to read/set data in some local system running on-premise.

Drag the appropriate block into the staging area and connect it up as required.

One of the input pins for the block will be the connector name. Here, you need to choose which connector you wish to connect with for running the action.

For a given connector type (like BACnet) you could have multiple connectors deployed (one connector in each building, for example).

So you need to choose which connector to use to run your action.

{% hint type="note" %}
    The connector name does not have to be decided while designing your model. It is a regular input pin so you can obtain the connector name dynamically by any other means and feed it as an input to the block.
    For example, you could name your connectors after the building they are deployed in.
    Then, when you need to get data from the building, you can take the building name from somewhere else and feed that as the name of the connector to get data from. {% endhint %}

If you don't have any connectors setup yet, you can easily set one up from the designer itself.

## Setting up a connector
To connect to an on-premise system like a building control system or a database, you first need to decide what type of connector you need (Modbus, Sql Server, etc...) and then register a new connector with a unique name.

You will then have to install a gateway on your local system for the connector you just registered.

Then, in an [action](actions.md#actions) in your model, you need to use a block for the connector and specify the name of the connector you wish to communicate with.

Lucy will automatically send requests to the corresponding gateway and get back responses.

You can do all of this easily from the [Model Designer](modeldesigner.md#model-designer) itself. 

Alternatively you can pre-configure your connectors and gateways and then build your models.


## Setting up a connector from [Model Designer](modeldesigner.md#model-designer)
You can easily setup a new connector from the model designer itself.
Just drag in a block for that connector. Under 'Connector Name', select `Add New +`.

You will be prompted to enter a connector name.
Once you do so, you will be given a link to download the connector gateway program as well as a 'configuration key' you can use to easily configure the gateway while it is being installed.

<a name='opconnectorlist'></a>

## Setting up a connector separately
Setting up the connector from the model designer is an easy way to get started. But you will likely want to do the setup independently of the Lucy model.
Especially if the model is being built in a different environment and then imported here.
You can explicitly setup a connector and install the gateway software without having to go through the model designer.
From the Lucy dashboard, open the image:: images/gear.png menu and then under **On-Premise Connectors** choose **View**.

You will be shown a list of all connectors that have been deployed.
You can click on any of them to edit their configuration.
On the right side is a link to add a new connector.

When adding a new connector, you will be prompted to choose the connector type and then give a name for the connector.
The connector name must be unique for a given connector type.

Once you register the connector, you will be taken to the connector's screen.
Here you can view details about the connector, including when it was last seen to be active.
(Connectors become active only if the gateway software is installed and connected to your Lucy account).

To install the gateway, click the **Install Connector** link in the sidebar.


## Installing a Gateway
When setting up the connctor, you will be given a link to download the connector gateway program.

Currently, all gateways run on Windows and require .NET Framework 4.6 or higher.

The gateways are distributed as msi files that can be deployed easily by simply executing the msi.
This will run the interactive setup to install the gateway software on the machine.


You can also remotely-deploy the msi by passing in appropriate command line parameters.

## Setting up the Gateway
During the interactive setup process, the gateway sofware will be installed in the machine and registered to run as a Windows Service.
It will run silently in the background and will launch whenever you start the machine.

During installation you will need to provide some details in order to let the gateway communicate with your Lucy account.

1. Your Lucy account url (https://myname.lucy.iviva.cloud or something like that)
2. An API Key. You can use the one you see in your default Lucy dashboard. You can alternatively generate/manage API Keys by going to the System application and then choosing 'API Keys' in the image:: images/gear.png menu.
3. The name of the connector - This should be the name you used when registering the connector.

As a quick way to do this - when you click the 'Install Connector' link in Lucy, it will show you a piece of text for you to copy.
You can copy that and paste it into the installation wizard to automatically setup these parameters.


Once these settings have been entered, a quick connectivity test will be performed by the installation process to ensure your settings are correct.


After this - you may be required to configure additional settings depending on the type of gateway being installed.

For example, if you are installing the Sql Server Connector, then you will need to provide a connection string to the database that you wish to connect to.

Once the configuration is done, the program will be installed and run as a service.

The program is installed in your PROGRAMFILES folder with the name of the connector type.

The folder contains a configuration file in JSON format and will also contain, by default, any log files generated by the gateway.

Once the gateway is running, you can view the status of it from the [](onpremiseconnectors.md#opconnectorlist).

## Diagnosing Problems and Monitoring
From the [](onpremiseconnectors.md#opconnectorlist) you can click on any connector to view details about it - including its last heart beat time.
Each connector sends a heartbeat to the server at regular intervals to notify the server that it is alive and healthy.
Heart beats are sent every 5minutes. Based on the last heart beat time that you see in the connector details screen, you will know if the connector is active or not.

On the computer where the connector gateway is installed, you can view log files that have been generated by the gateway.


## Architecture and Security
The connector gateways need to be run as NT Services. They are typically installed and run as a Local System Account.
You will require administrative privileges to run the installer program.
Once the service is installed, it will need write access to the logs directory that you have configured when setting up the gateway (it defaults to the folder where the program is installed).
The connector makes outbound https connections to your Lucy server - so you will need to enable your network to allow the gateway to talk to that server over SSL.
In addition, there may be other security and network requirements for the connector based on its nature.

For example, the Sql Server connector requires network access to the sql server database that you will connect to.
The ModBus connector requires LAN access to where the controllers are typically running.