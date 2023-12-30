


[importexport:](importexport:)

# Exporting and Importing your Models
It's a good idea to export and backup your work regularly.
You'll also need to export it if you want to transfer it to a different server (going from staging to production, etc...).

You can export your models and user interfaces as a single package.
That package can later be imported into a different environment.

## Exporting models
To export models, go to the Lucy dashboard, click the image:: images/gear.png icon and choose click **Export**.

The export screen lets you specify a model (or multiple models separated by commas) and then export them all together.

You can either export only the specified models (**not** recommended) or find all the related dependencies and export all of them (much better!).


After entering the models you want to export in the text box, click the **Find Dependencies** button. This will do a check on your model to see what other models it depends on, it then recursively checks all those models as well until it has a full list of all models required to make the system work.

You will then get a list of all these models with checkboxes to individually disable any items you don't want to export [#]_

Select all the models and then click the **Export** button at the bottom.

All the selected models will be exported together as a single JSON file.

{% hint type="note" %}
    To find dependencies, you need to have opened and saved your model at least once. {% endhint %}

{% hint type="note" %}
    If you want to export all your models, leave the textbox blank and just hit the **Export** button. {% endhint %}

.. rubric:: Footnotes

.. [#] The only reason to do this if you did some updates to the model on the new server you plan on transferring the models to and don't want those changes overwritten. i.e,you have out-of-date versions of some models combined with updated versions of others - does that sound like a good idea to you? Me neither.

## Import Models
You can import the package that you exported to recover a backup or transfer your setup to a new environment.

Go to the |Lucy| dashboard, click the image:: images/gear.png icon and then select **Import**.

In the next screen, you can upload the package file - either click in the giant box in the middle of the screen and select the file, or just drag it into the box.

You can also optionally specify a comma separated list of which models you specifically want to import from the package.

When you are ready, hit the **Import** button to import the models.

If the import process detected that your models have references to other models which are not part of the package, then an error will be raised and nothing will be imported.