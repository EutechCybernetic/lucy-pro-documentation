


<a name='bulkloading'></a>

# Bulk Loading and Importing Data
You can use Lucy to bulk import data from Excel spreadsheets.

Two common scenarios:

1. Uploading data in bulk to create model instances
2. Uploading data to repeatedy execute an [action](actions)


Both scenarios use the same underlying technique.

## Uploading Data

To upload data in bulk, click on the [Model Actions](modelactions) icon in the toolbar and then choose 'Bulk Load Data'.

<figure><img src=' images/bulkimport.png'></figure>


In the bulk import screen, you can see a list of currently importing items and their status.

Click the image:: images/attradd.png icon to upload a new Excel sheet.

Once the sheet is uploaded, Lucy will call an [action](actions) called code/BulkLoad in your model, once for every row in the excel sheet.

{% hint type="note" %}
    The action name that is called is fixed as code/BulkLoad
    To have your model support multiple types of bulk imports, read the section on [multipleimports](multipleimports) {% endhint %}

The action will be sent a parameter for every column in the sheet. The column name will be used as the name of the parameter and the value will be the value of that cell in each row.

Your action can then make use of that data in any way.
If you are creating new model instances, then you can mark the action as *Trigger new instance* and then wire up all the parameters to |attributeset| blocks to assign attribute values from the sheet.

If you are using the action sequence to do a custom import of iviva application data, then you can process that data and call iviva services using the [callservice-ref](callservice-ref) block.

## Error Handling
If any error occurs in your action and the action sequence terminates, then that particular record in the Excel sheet will be marked as an error and the import process will move on to the next row.
At the end, from the same bulk-import screen, you can download the excel sheet with a new **Errors** column at the end showing the error that was raised for that particular row. You can then fix the error (or fix the action sequence as the case may be) and then upload again.

{% hint type="note" %}
    You need to take care of handling multiple uploads of the same data. Your action sequence needs to incorporate logic to check if that particular piece of data was already uploaded or not. A good way to check this is to require some unique column in the sheet, and then run a [data source](datasources) query to check if an item having that unique attribute already exists and if so, do an update to the existing item instead of creating a new one. {% endhint %}

## Downloading Empty Templates
It's a good idea to make it possible to download an empty excel sheet  that acts as a template for filling data. That will help guide your user towards filling the sheet in the correct way.
The bulk-import screen has a sidebar link to downlaod an empty template.
When the link is clicked, an action called code/DownloadBulkTemplate will be called in your model. You should then create an excel sheet and return it as binary data.

To generate the excel sheet, use the [genexcel](genexcel) function inside a javascript block.

Use a [actionbinaryoutput-ref](actionbinaryoutput-ref) block to return the data back.

See [binarydata](binarydata) for more information on working with binary data.


<a name='multipleimports'></a>

## Supporting Multiple Bulk Import Actions
It's possible to have more than one bulk-load and template-download action in your model.

The default actions are called code/BulkLoad and code/DownloadBulkLoadTemplate respectively.

If you visit the bulk import page and specify a code/prefix query string parameter to the bulk-import page, you can have it use actions called code/BulkLoad<prefix> and code/Download<prefix>BulkLoadTemplate respectively.

For example, if you add code/&prefix=EnergyData  to the bulk-import screen utl:

```

    http://<ivivacloudurl>/Apps/System/bulkloadmetadata?key=112&prefix=EnergyData

```

Then the importer will look for an action in your model called code/BulkLoadEnergyData.
The empty template download link will look for an action called code/DownloadEnergyDataBulkLoadTemplate


## Excel Sheet Format
For bulk imports to work, the Excel sheet must have a suitable format:

1. The file format should be code/.xlsx (Excel 2007 or above)
2. The first row should have column headers in them
3. All other rows should contain data

{% hint type="note" %}
    If your import logic needs to work with a variable number of columns, instead of specifying individual column names as parameters to the [Action Start](actionstart-ref) block, use the *All Output* pin to read all values together as a dictionary and then use that to probe for what keys are present (using either a |javascript| block or an [exists-ref](exists-ref) block) {% endhint %}