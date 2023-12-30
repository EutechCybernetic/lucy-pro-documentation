

[datacollections:](datacollections:)

================
# Data Collections

Often times when building an integration scenario, you need to be able to store, query and retrieve arbitrary bits of data.

Some examples of things you might need to store:

* Mapping from users in Lucy to users in an HR system
* Storing details about devices including their IP addresses or other information required to communicate with them
* Storing the status of various requests and objects created by users.

Data Collections are perfect for this task.

A data collection is essentially a container for storing arbitrary documents.
You can add documents to a collection, delete and update documents from a collection as well as query the collection to retreive documents that match a certain criteria.

Each document in a collection is just a JSON-based object.
There is no fixed structure or schema for a collection.
Each model can have multiple collections. 

{% hint style="info" %}

    Even though you could, in theory, store all your data in one large collection, it is generally recommended to have different collections for different kinds of data.
    Even though there is no structure imposed on each document in a collection, in practice, it's recommended that all documents in a collection share the same structure.

{% endhint %}

There two entities involved in *Data Collections*,

1. `Collection`_
2. `Attributes`_

# Collection

A collection is the container in which you store your aribitrary data. Let's look at some of the operations you can perform on a collection.

## Creating a Collection

The following steps illustrate creating a data collection,

1. Open model collections
2. Choose *Create a collection*
3. Give a name & press **Enter** or the tick icon
4. To *cancel*, click on **Delete** button or press **Escape**

You should see the following result,

<figure><img src=' images/data-collections/create-collection-result.png'></figure>

**Illustration:**

<figure><img src=' images/data-collections/create-collection.gif'></figure>

## Updating a Collection

The following steps illustrate modifying a collection name,

1. Choose the created collection by clicking on the *eye* icon,
2. Click on **Edit** button next to the collection name in *Configure* pane
3. Give a name & press **Enter** or the tick icon
4. To *cancel*, click on **Close** button or press **Escape**

**Illustration:**

<figure><img src=' images/data-collections/update-collection.gif'></figure>

## Deleting a Collection

The following steps illustrate deleting a collection,

1. Choose the created collection by clicking on the *eye* icon,
2. Click on **Edit** button next to the collection name in *Configure* pane
3. Click on **Delete** button next to *Collection Name*
4. To *cancel*, click on **Close** button or press **Escape**

**Illustration:**

<figure><img src=' images/data-collections/delete-collection.gif'></figure>

# Attributes

Attributes give the collection a structure & general sense about the data the collection stores. Let's look at some of the operations you can perform on a collection.

## Creating an Attribute

The following steps illustrate creating attributes,

1. Choose the created collection by clicking on the *eye* icon,
2. Click on *Add Attribute* in the *Configure* pane
3. Give a name & press **Enter** or the tick icon
4. To *cancel*, click on **Delete** button or press **Escape**

You should see the following result,

<figure><img src=' images/data-collections/create-attribute-result.png'></figure>

**Illustration:**

<figure><img src=' images/data-collections/create-attributes.gif'></figure>

## Updating an Attribute

The following steps illustrate modifying an attribute name,

1. Choose the created collection by clicking on the *eye* icon,
2. Click on an attribute from *Attributes* list in the *configure* pane
3. Give a name & press **Enter** or the tick icon
4. To *cancel*, click on **Close** button or press **Escape**

**Illustration:**

<figure><img src=' images/data-collections/update-attributes.gif'></figure>

## Deleting an Attribute

The following steps illustrate deleting a collection,

1. Choose the created collection by clicking on the *eye* icon,
2. Click on an attribute from *Attributes* list in the *configure* pane
3. Click on **Delete** button to remove the attribute
4. To *cancel*, click on **Close** button or press **Escape**

**Illustration:**

<figure><img src=' images/data-collections/delete-attribute.gif'></figure>

. note::

    Your collection is document based and loosely structured. This means you can store any attributes and data you want in it - you are not restricted to the attributes you have defined.
    The main reason for explicitly defining attributes is for documenting the intention of your data collection and to make it easy for Lucy to present configuration to you.


# Working with Collections

So far, we saw how to define a collection & attributes. To actually write data into the collection & work on the data, you need to either use one of the blocks related to data collections or use our [Javascript](es6javascript-ref) api.

1. [Using lucy data collection blocks](lucy-data-collection-blocks)
2. [Using Javascript data collection API](js-data-collection-api)

[lucy-data-collection-blocks:](lucy-data-collection-blocks:)

## Lucy Data Collection Blocks

Data collection blocks are  Lucy blocks, that enable you to work with the collection you created earlier visually. The following blocks are provided for you and we will go through each of them in detail,

1. `Insert one document`_
2. `Insert all documents`_
3. `Find one document`_
4. `Find all documents`_
5. `Update one document`_
6. `Update all documents`_
7. `Replace one document`_
8. `Delete one document`_
9. `Delete all documents`_
10. `Count all documents`_

### Insert one document

This block allows you to insert one document at a time. *Document* here can be explained with a simple analogy. If you have details about 10 users from **User 1** to **User 10**, then each detail here can be consisdered a *document*. A document is a simple **JSON** structure, that looks like the following,

.. code:: json

    {
        "FirstName": "John",
        "LastName": "Doe",
#####         "Email": "john.doe@example.com"

The following steps illustrate how you can insert a document,

1. From the blocks menu, choose **Collections** -> **Insert one document** & add it to you lucy action
2. From the block's property menu, choose a collection from **Collection Name** dropdown
3. You can insert a document in couple of ways,
    1. Pass a JSON structure (*default*)
        1. Uncheck the **Update data as attributes** option from the block's property menu.
        2. Use [Make JSON Block](jsonobject-ref), [Javascript Block](javascript-ref) or [ES6 Javascript Block](es6javascript-ref) to construct your **JSON document**
        3. Pass the *output* from the above block into *Data* pin of this block
    2. Pass individual attributes
        1. Check the **Update data as attributes** option from the block's property menu.
        2. Set all input pins (*not required*) except *Data* pin in this block

{% hint type="note" %}
    Regardless of how you insert a *document*, it gets stored in the **JSON** structure described above. {% endhint %}

On the executing the action, you should see the following output for both methods described above,

.. code:: json

    {
        "_id": "5e21b3aecee5d8514cbfefa0",
        "FirstName": "John",
        "LastName": "Doe",
#####         "Email": "john.doe@example.com"

**Illustration**

<figure><img src=' images/data-collections/blocks/insert-1-doc.png'></figure>

### Insert all documents

This block allows you to insert multiple documents at a time. The following steps illustrate how you can insert all documents,

1. From the blocks menu, choose **Collections** -> **Insert all documents** & add it to you lucy action
2. From the block's property menu, choose a collection from **Collection Name** dropdown
3. Use [Make JSON Array Block](jsonarray-ref), [Javascript Block](javascript-ref) or [ES6 Javascript Block](es6javascript-ref) to construct your **JSON document**
4. Pass the *output* from the above block into *Data* pin of this block 

<figure><img src=' images/data-collections/blocks/insert-n-doc.png'></figure>

### Filter Configuration

.. |icon-filter-add-group| image:: images/data-collections/blocks/icon-filter-add-group.png
.. |icon-filter-add-condition| image:: images/data-collections/blocks/icon-filter-add-condition.png

Except for *Insert one document* and *Insert all documents* blocks, all the others have a common feature, which is the ability to perform an action on the collection based on *filter* conditions. Now, the filter conditions can be passed in a couple of ways,
    1. Using UI based filter
    2. Using *Filter* input pin

###### UI Filter

We will focus on UI filter configuration.

To access the filter configuration, click on *Configure Collection* in the block's property editor or double on the block.

<figure><img src=' images/data-collections/blocks/filter-menu.png'></figure>

The following illustrates a sample filter configuration,

<figure><img src=' images/data-collections/blocks/filter-sample-detailed.png'></figure>

You could see from the sample that *filter conditions* aren't flat, but nested within *filter groups*. This allows a rich & intuitive control over filtering your data. All *filter conditions* & *filter groups* are inside a default group called *super group*.

To add a *filter condition*,

1. Click on |icon-filter-add-condition|
2. Choose a value from the first dropdown box. These are your *attributes* from the collection
3. Choose a filter condition from available options
4. Use *Pin/Value* toggle switch, to either take the filter value from one of the block's input pins (*default*) or from a harcoded value

To add a *filter group*,

1. Click on |icon-filter-add-group|
2. Use *Either/All* toggle switch to decide if *either* or *all* the *sub filter conditions* & *sub filter groups* should pass for a successful match

The above process can go on repeatedly based on your filter requirements. Once you are done, you can see the raw query with *Preview*, save the changes with *Save* or discard the changes with *Cancel*.

###### Passing via Filter Input Pin

Right now data collections are powered by *MongoDB* in the backend. So, to pass a filter via input, you could use [Make JSON Block](jsonobject-ref), [Javascript Block](javascript-ref) or [ES6 Javascript Block](es6javascript-ref) to construct your **JSON document**. Checkout the available filter options `here <https://docs.mongodb.com/manual/reference/operator/query/>`_. Few sample filters are given below,

1. Match all documents whose *FirstName* is *John*

.. code:: json

    {
#####         {"FirstName": {"$eq": "John"}}

2. Match all documents whose *FirstName* is *John* and *LastName* is *Doe*

.. code:: json

    {
        "$and": [
            {"FirstName": {"$eq": "John"}},
##### #######             {"LastName": {"$eq": "Doe"}},

3. Match all documents whose *FirstName* is *John* or *LastName* is *Doe* or if the *Age* is between 20 and 30

.. code:: json

    {
        "$or": [
            {"FirstName": {"$eq": "John"}},
####             {"LastName": {"$eq": "Doe"}},
                "$and": [
                    {"Age": {"$gt": 20}},
##### #######                     {"Age": {"$lt": 30}}
#####         ],

### Find one document

This block allows you to find the first matching document from your data collection based on the filter conditions provided. The following steps illustrate how you can find a document,

1. From the blocks menu, choose **Collections** -> **Find one document** & add it to you lucy action
2. From the block's property menu, choose a collection from **Collection Name** dropdown
3. Filters can be passed in couple of ways,
    1. Pass filter as input
        1. Check *Take filter from pin* property of the block
        2. Pass the data to *Filter* input pin
    2. Take filter from configuration (*default*)
        1. Uncheck *Take filter from pin* property of the block
        2. Configure the filter as detailed  in `Filter Configuration`_ section
4. Outputs can be processed in the either of the follow ways,
    1. Extract collection's attributes as separate output pins
        1. Check *Receive Individual Fields* property of the block
        2. Attributes available at their respective output pins
    2. Extract entire document (*default*)
        1. Uncheck *Receive Individual Fields* property of the block
        2. The entire document which would be available at available at *All Output* pin

**Illustration**

<figure><img src=' images/data-collections/blocks/find-1-doc.png'></figure>

### Find all documents

This block allows you to find all matching documents from your data collection based on the filter conditions provided. The following steps illustrate how you can find all documents,

1. From the blocks menu, choose **Collections** -> **Find all documents** & add it to you lucy action
2. From the block's property menu, choose a collection from **Collection Name** dropdown
3. Filters can be passed in couple of ways,
    1. Pass filter as input
        1. Check *Take filter from pin* property of the block
        2. Pass the data to *Filter* input pin
    2. Take filter from configuration (*default*)
        1. Uncheck *Take filter from pin* property of the block
        2. Configure the filter as detailed  in `Filter Configuration`_ section

**Illustration**

<figure><img src=' images/data-collections/blocks/find-n-doc.png'></figure>

### Update one document

This block allows you to update the first matching document in your data collection based on the data & filter conditions provided. The following steps illustrate how you can update a document,

1. From the blocks menu, choose **Collections** -> **Update one document** & add it to you lucy action
2. From the block's property menu, choose a collection from **Collection Name** dropdown
3. Filters can be passed in couple of ways,
    1. Pass filter as input
        1. Check *Take filter from pin* property of the block
        2. Pass the data to *Filter* input pin
    2. Take filter from configuration (*default*)
        1. Uncheck *Take filter from pin* property of the block
        2. Configure the filter as detailed  in `Filter Configuration`_ section
4. Data can be passed in couple of ways,
    1. Update individual attributes
        1. Check *Update data as attributes* property of the block
        2. Pass value the for the attributes at their respective input pins
    2. Pass entire document (*default*)
        1. Uncheck *Update data as attributes* property of the blocks
        2. Pass the document to *Data* input pin

**Sample Output**

.. code:: json

    {
        matchedCount: 1,
#####         modifiedCount: 1

{% hint type="note" %}
    Here, *modifiedCount* could be **0**, if matching document was found, but data passed is same as the existing one. {% endhint %}

{% hint type="note" %}
    If no documents match the given filter, then a new document is created in the collection. In which case you will see the following output, {% endhint %}

    .. code:: json

        {
            "matchedCount": 0,
            "modifiedCount": 0,
#####             "_id": "5e25b5636725d689afccf6e7"

**Illustration**

<figure><img src=' images/data-collections/blocks/update-1-doc.png'></figure>

### Update all documents

This block allows you to update all matching documents in your data collection based on the data & filter conditions provided. The following steps illustrate how you can update all documents,

1. From the blocks menu, choose **Collections** -> **Update all documents** & add it to you lucy action
2. From the block's property menu, choose a collection from **Collection Name** dropdown
3. Filters can be passed in couple of ways,
    1. Pass filter as input
        1. Check *Take filter from pin* property of the block
        2. Pass the data to *Filter* input pin
    2. Take filter from configuration (*default*)
        1. Uncheck *Take filter from pin* property of the block
        2. Configure the filter as detailed  in `Filter Configuration`_ section
4. Data can be passed in couple of ways,
    1. Update individual attributes
        1. Check *Update data as attributes* property of the block
        2. Pass value the for the attributes at their respective input pins
    2. Pass entire document (*default*)
        1. Uncheck *Update data as attributes* property of the blocks
        2. Pass the document to *Data* input pin

{% hint type="note" %}
    If no documents match the given filter, then a new document is created in the collection. {% endhint %}

**Illustration**

<figure><img src=' images/data-collections/blocks/update-n-doc.png'></figure>

### Replace one document

This block allows you to delete the first matching document entirely in your data collection based on the data & filter conditions provided. The following steps illustrate how you can replace a document,

1. From the blocks menu, choose **Collections** -> **Replace one document** & add it to you lucy action
2. From the block's property menu, choose a collection from **Collection Name** dropdown
3. Filters can be passed in couple of ways,
    1. Pass filter as input
        1. Check *Take filter from pin* property of the block
        2. Pass the data to *Filter* input pin
    2. Take filter from configuration (*default*)
        1. Uncheck *Take filter from pin* property of the block
        2. Configure the filter as detailed  in `Filter Configuration`_ section
4. Data can be passed in couple of ways,
    1. Update individual attributes
        1. Check *Update data as attributes* property of the block
        2. Pass value the for the attributes at their respective input pins
    2. Pass entire document (*default*)
        1. Uncheck *Update data as attributes* property of the blocks
        2. Pass the document to *Data* input pin

{% hint type="note" %}
    The main difference from `Update one document`_ is that, you can *replace* entire document with a new one. But, with `Update one document`_ you can update individual fields in the document. {% endhint %}

    For example, if you *update* the document *{"FirstName": "John", "LastName": "Doe"}* with *{"Age": 28}*, the final state of the document would be *{"FirstName": "John", "LastName": "Doe", "Age": 28}*.

    While, if you *replace* the document *{"FirstName": "John", "LastName": "Doe"}* with *{"Age": 28}*, the final state of the document would be *{"Age": 28}*.

**Sample Output**

.. code:: json

    {
        matchedCount: 1,
#####         modifiedCount: 1

{% hint type="note" %}
    If no documents match the given filter, then a new document is created in the collection. In which case you will see the following output, {% endhint %}

    .. code:: json

        {
            "matchedCount": 0,
            "modifiedCount": 0,
#####             "_id": "5e25b5636725d689afccf6e7"

**Illustration**

<figure><img src=' images/data-collections/blocks/replace-1-doc.png'></figure>

### Delete one document

This block allows you to delete the first matching document in your data collection based on the filter conditions provided. The following steps illustrate how you can delete a document,

1. From the blocks menu, choose **Collections** -> **Delete one document** & add it to you lucy action
2. From the block's property menu, choose a collection from **Collection Name** dropdown
3. Filters can be passed in couple of ways,
    1. Pass filter as input
        1. Check *Take filter from pin* property of the block
        2. Pass the data to *Filter* input pin
    2. Take filter from configuration (*default*)
        1. Uncheck *Take filter from pin* property of the block
        2. Configure the filter as detailed  in `Filter Configuration`_ section

**Illustration**

<figure><img src=' images/data-collections/blocks/delete-1-doc.png'></figure>

### Delete all documents

This block allows you to delete all the matching documents in your data collection based on the filter conditions provided. The following steps illustrate how you can delete all documents,

1. From the blocks menu, choose **Collections** -> **Delete all document** & add it to you lucy action
2. From the block's property menu, choose a collection from **Collection Name** dropdown
3. Filters can be passed in couple of ways,
    1. Pass filter as input
        1. Check *Take filter from pin* property of the block
        2. Pass the data to *Filter* input pin
    2. Take filter from configuration (*default*)
        1. Uncheck *Take filter from pin* property of the block
        2. Configure the filter as detailed  in `Filter Configuration`_ section

**Illustration**

<figure><img src=' images/data-collections/blocks/delete-n-doc.png'></figure>

### Count all documents

This block allows you to count all the matching documents in your data collection based on the filter conditions provided. The following steps illustrate how you can count all documents,

1. From the blocks menu, choose **Collections** -> **Count all documents** & add it to you lucy action
2. From the block's property menu, choose a collection from **Collection Name** dropdown
3. Filters can be passed in couple of ways,
    1. Pass filter as input
        1. Check *Take filter from pin* property of the block
        2. Pass the data to *Filter* input pin
    2. Take filter from configuration (*default*)
        1. Uncheck *Take filter from pin* property of the block
        2. Configure the filter as detailed  in `Filter Configuration`_ section

**Illustration**

<figure><img src=' images/data-collections/blocks/count-n-doc.png'></figure>

[js-data-collection-api: ](js-data-collection-api: )

## Javascript Data Collection API

When you need more control while passing data to your collection or when processing the outputs, you can make use of *Data Collection API* provided via [ES6 Javascript Block](es6javascript-ref). The following *API's* are provided for you and we will go through each of them in detail,

1. `insertOne`_
2. `insertMany`_
3. `findOne`_
4. `findMany`_
5. `updateOne`_
6. `updateMany`_
7. `replaceOne`_
8. `deleteOne`_
9. `deleteMany`_
10. `count`_
11. `aggregate`_

{% hint style="info" %}

    Since, data colletions are part of the Lucy model, they are exposed under the model in ES6 Javascript block. To access them, you could do as follows,

{% endhint %}

    .. code:: javascript

        let model = lucy.currentModel();
        // or,
        // let model = lucy.model("<model_name>");
        let collections = model.collections();

{% hint style="info" %}

    All the API's below return a Javascript Promise, you can checkout more details about it & how to use them [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises).

{% endhint %}

### insertOne

Insert one document at a time. 

**Syntax**

.. code:: javascript

    collections.insertOne("<collection_name>", "<document>", "<options>");

.. list-table:: Input Parameters
    :header-rows: 1

    * - Name
      - Data Type
      - Required
      - Description
    * - *collection_name*
      - [Text](dt-text)
      - *true*
      - Name of the collection to store the document under
    * - *document*
      - [JSON document](dt-json)
      - *true*
      - Document to be stored
    * - *options*
      - [JSON document](dt-json)
      - *true* (can be empty with no fields like **{}**)
      - `Arbitrary Options`_ to be passed to the data collection API

.. list-table:: Output
    :header-rows: 1

    * - Data Type
      - Description
    * - [JSON document](dt-json)
      - Document that was inserted into the collection

        .. code:: json

            {
                "_id": "5e21b3aecee5d8514cbfefa0",
                "FirstName": "John",
                "LastName": "Doe",
#####                 "Email": "john.doe@example.com"

**Example**

.. code:: javascript

    let model = lucy.currentModel();
    // or,
    // let model = lucy.model("UserModel");
    let collections = model.collections();
    let document = {
        "FirstName": "John",
        "LastName": "Doe",
        "Email": "john.doe@example.com"
    };
    let options = {};
    
    collections.insertOne("User", document, options)
        .then(result => {
            runtime.done({});
        })
        .catch(error => {
            runtime.error(error);
        });

### insertMany

Insert multiple documents at a time. 

**Syntax**

.. code:: javascript

    collections.insertMany("<collection_name>", "<documents>", "<options>");

.. list-table:: Input Parameters
    :header-rows: 1

    * - Name
      - Data Type
      - Required
      - Description
    * - *collection_name*
      - [Text](dt-text)
      - *true*
      - Name of the collection to store the documents under
    * - *documents*
      - [JSON document](dt-json)
      - *true*
      - Array of documents to be stored
    * - *options*
      - [JSON document](dt-json)
      - *true* (can be empty with no fields like **{}**)
      - `Arbitrary Options`_ to be passed to the data collection API

**Example**

.. code:: javascript

    let model = lucy.currentModel();
    // or,
    // let model = lucy.model("UserModel");
    let collections = model.collections();
####     let documents = [
            "FirstName": "John",
            "LastName": "Doe",
            "Email": "john.doe@example.com"
####         },
            "FirstName": "Jane",
            "LastName": "Doe",
            "Email": "jane.doe@example.com"
####         },
            "FirstName": "Josh",
            "LastName": "Doe",
#####             "Email": "josh.doe@example.com"
    ];
    let options = {};
    
    collections.insertMany("User", documents, options)
        .then(result => {
            runtime.done({});
        })
        .catch(error => {
            runtime.error(error);
        });

### findOne

Find the first matching document for the given collection & filter condition. More information on `Filter Configuration`_.

**Syntax**

.. code:: javascript

    collections.findOne("<collection_name>", "<filter>", "<options>");

.. list-table:: Input Parameters
    :header-rows: 1

    * - Name
      - Data Type
      - Required
      - Description
    * - *collection_name*
      - [Text](dt-text)
      - *true*
      - Name of the collection to find the documents
    * - *filter*
      - [JSON document](dt-json)
      - *true*
      - Filter condition to filter documents by
    * - *options*
      - [JSON document](dt-json)
      - *true* (can be empty with no fields like **{}**)
      - `Arbitrary Options`_ to be passed to the data collection API

.. list-table:: Output
    :header-rows: 1

    * - Data Type
      - Description
    * - [JSON document](dt-json)
      - First document that matched the filter condition

        .. code:: json

            {
                "_id": "5e21b3aecee5d8514cbfefa0",
                "FirstName": "John",
                "LastName": "Doe",
#####                 "Email": "john.doe@example.com"

**Example**

.. code:: javascript

    let model = lucy.currentModel();
    // or,
    // let model = lucy.model("UserModel");
    let collections = model.collections();
    let filter = {
        {"FirstName": {"$eq": "John"}}
    };
    let options = {};
    
    collections.findOne("User", filter, options)
        .then(result => {
            // process result
            runtime.done({});
        })
        .catch(error => {
            runtime.error(error);
        });

### findMany

Find all matching documents for the given collection & filter condition. More information on `Filter Configuration`_.

**Syntax**

.. code:: javascript

    collections.findMany("<collection_name>", "<filter>", "<options>");

.. list-table:: Input Parameters
    :header-rows: 1

    * - Name
      - Data Type
      - Required
      - Description
    * - *collection_name*
      - [Text](dt-text)
      - *true*
      - Name of the collection to find the documents
    * - *filter*
      - [JSON document](dt-json)
      - *true*
      - Filter condition to filter documents by
    * - *options*
      - [JSON document](dt-json)
      - *true* (can be empty with no fields like **{}**)
      - `Arbitrary Options`_ to be passed to the data collection API

.. list-table:: Output
    :header-rows: 1

    * - Data Type
      - Description
    * - [JSON document](dt-json)
      - Array of documents that matched the filter condition

        .. code:: json

####             [
                    "_id": "5e21b3aecee5d8514cbfefa0",
                    "FirstName": "John",
                    "LastName": "Doe",
                    "Email": "john.doe@example.com"
####                 },
                    "_id": "5e21b3aecee5d8514cbfefa1",
                    "FirstName": "Jane",
                    "LastName": "Doe",
                    "Email": "jane.doe@example.com"
####                 },
                    "_id": "5e21b3aecee5d8514cbfefa2",
                    "FirstName": "Josh",
                    "LastName": "Doe",
####### #####                     "Email": "josh.doe@example.com"

**Example**

.. code:: javascript

    let model = lucy.currentModel();
    // or,
    // let model = lucy.model("UserModel");
    let collections = model.collections();
    let filter = {
        {"FirstName": {"$eq": "John"}}
    };
    let options = {};
    
    collections.findOne("User", filter, options)
        .then(result => {
            // process result
            runtime.done({});
        })
        .catch(error => {
            runtime.error(error);
        });

### updateOne

Update first matching document with the given data for the given collection & filter condition. More information on `Filter Configuration`_.

{% hint type="note" %}
    If no documents match the given filter, then a new document is created in the collection. In which case you will get the following output, {% endhint %}

    .. code:: json

        {
            "matchedCount": 0,
            "modifiedCount": 0,
#####             "_id": "5e25b5636725d689afccf6e7"

**Syntax**

.. code:: javascript

    collections.updateOne("<collection_name>", "<filter>", "<data>", "<options>");

.. list-table:: Input Parameters
    :header-rows: 1

    * - Name
      - Data Type
      - Required
      - Description
    * - *collection_name*
      - [Text](dt-text)
      - *true*
      - Name of the collection to update the documents for
    * - *filter*
      - [JSON document](dt-json)
      - *true*
      - Filter condition to filter documents by
    * - *data*
      - [JSON document](dt-json)
      - *true*
      - Document to be updated with
    * - *options*
      - [JSON document](dt-json)
      - *true* (can be empty with no fields like **{}**)
      - `Arbitrary Options`_ to be passed to the data collection API

.. list-table:: Output
    :header-rows: 1

    * - Data Type
      - Description
    * - [JSON document](dt-json)
      - Replacement result

        .. code:: json

            {
                matchedCount: 1,
#####                 modifiedCount: 1

        **Note**

        Here, *modifiedCount* could be **0**, if matching document was found, but data passed is same as the existing one.

**Example**

.. code:: javascript

    let model = lucy.currentModel();
    // or,
    // let model = lucy.model("UserModel");
    let collections = model.collections();
    let filter = {
        {"FirstName": {"$eq": "John"}}
    };
    let data = {
        {"LastName": "Carpenterr"}
    };
    let options = {};
    
    collections.updateOne("User", filter, data, options)
        .then(result => {
            // process result
            runtime.done({});
        })
        .catch(error => {
            runtime.error(error);
        });

### updateMany

Update all matching documents with the given data for the given collection & filter condition. More information on `Filter Configuration`_.

{% hint type="note" %}
    If no documents match the given filter, then a new document is created in the collection. In which case you will get the following output, {% endhint %}

    .. code:: json

        {
            "matchedCount": 0,
            "modifiedCount": 0,
#####             "_id": "5e25b5636725d689afccf6e7"

**Syntax**

.. code:: javascript

    collections.updateMany("<collection_name>", "<filter>", "<data>", "<options>");

.. list-table:: Input Parameters
    :header-rows: 1

    * - Name
      - Data Type
      - Required
      - Description
    * - *collection_name*
      - [Text](dt-text)
      - *true*
      - Name of the collection to update the documents under for
    * - *filter*
      - [JSON document](dt-json)
      - *true*
      - Filter condition to filter documents by
    * - *data*
      - [JSON document](dt-json)
      - *true*
      - Document to be updated with
    * - *options*
      - [JSON document](dt-json)
      - *true* (can be empty with no fields like **{}**)
      - `Arbitrary Options`_ to be passed to the data collection API

.. list-table:: Output
    :header-rows: 1

    * - Data Type
      - Description
    * - [JSON document](dt-json)
      - Replacement result

        .. code:: json

            {
                matchedCount: 10,
#####                 modifiedCount: 10

**Example**

.. code:: javascript

    let model = lucy.currentModel();
    // or,
    // let model = lucy.model("UserModel");
    let collections = model.collections();
    let filter = {
        {"FirstName": {"$eq": "John"}}
    };
    let data = {
        {"LastName": "Carpenterr"}
    };
    let options = {};
    
    collections.updateMany("User", filter, data, options)
        .then(result => {
            // process result
            runtime.done({});
        })
        .catch(error => {
            runtime.error(error);
        });

### replaceOne

Replace first matching document is replaced with the given data for the given collection & filter condition. More information on `Filter Configuration`_.

{% hint type="note" %}
    If no documents match the given filter, then a new document is created in the collection. In which case you will get the following output, {% endhint %}

    .. code:: json

        {
            "matchedCount": 0,
            "modifiedCount": 0,
#####             "_id": "5e25b5636725d689afccf6e7"

{% hint type="note" %}
    The main difference from `Update one document`_ is that, you can *replace* entire document with a new one. But, with `Update one document`_ you can update individual fields in the document. {% endhint %}

    For example, if you *update* the document *{"FirstName": "John", "LastName": "Doe"}* with *{"Age": 28}*, the final state of the document would be *{"FirstName": "John", "LastName": "Doe", "Age": 28}*.

    While, if you *replace* the document *{"FirstName": "John", "LastName": "Doe"}* with *{"Age": 28}*, the final state of the document would be *{"Age": 28}*.

**Syntax**

.. code:: javascript

    collections.replaceOne("<collection_name>", "<filter>", "<data>", "<options>");

.. list-table:: Input Parameters
    :header-rows: 1

    * - Name
      - Data Type
      - Required
      - Description
    * - *collection_name*
      - [Text](dt-text)
      - *true*
      - Name of the collection to replace the documents in
    * - *filter*
      - [JSON document](dt-json)
      - *true*
      - Filter condition to filter documents by
    * - *data*
      - [JSON document](dt-json)
      - *true*
      - Document to be replaced with
    * - *options*
      - [JSON document](dt-json)
      - *true* (can be empty with no fields like **{}**)
      - `Arbitrary Options`_ to be passed to the data collection API

.. list-table:: Output
    :header-rows: 1

    * - Data Type
      - Description
    * - [JSON document](dt-json)
      - Replacement result

        .. code:: json

            {
                matchedCount: 1,
#####                 modifiedCount: 1

        **Note**
        
        Here, *modifiedCount* could be **0**, if matching document was found, but data passed is same as the existing one.

**Example**

.. code:: javascript

    let model = lucy.currentModel();
    // or,
    // let model = lucy.model("UserModel");
    let collections = model.collections();
    let filter = {
        {"FirstName": {"$eq": "John"}}
    };
    let data = {
        {"FirstName": "Default"},
        {"LastName": "User"},
        {"Email": "default-user@example.com}
    };
    let options = {};
    
    collections.replaceOne("User", filter, data, options)
        .then(result => {
            // process result
            runtime.done({});
        })
        .catch(error => {
            runtime.error(error);
        });

### deleteOne

Delete first matching document for the given collection & filter condition. More information on `Filter Configuration`_.

**Syntax**

.. code:: javascript

    collections.deleteOne("<collection_name>", "<filter>", "<options>");

.. list-table:: Input Parameters
    :header-rows: 1

    * - Name
      - Data Type
      - Required
      - Description
    * - *collection_name*
      - [Text](dt-text)
      - *true*
      - Name of the collection to delete the documents from
    * - *filter*
      - [JSON document](dt-json)
      - *true*
      - Filter condition to filter documents by
    * - *options*
      - [JSON document](dt-json)
      - *true* (can be empty with no fields like **{}**)
      - `Arbitrary Options`_ to be passed to the data collection API

**Example**

.. code:: javascript

    let model = lucy.currentModel();
    // or,
    // let model = lucy.model("UserModel");
    let collections = model.collections();
    let filter = {
        {"FirstName": {"$eq": "John"}}
    };
    let options = {};
    
    collections.deleteOne("User", filter, options)
        .then(result => {
            // process result
            runtime.done({});
        })
        .catch(error => {
            runtime.error(error);
        });

### deleteMany

Delete all matching documents for the given collection & filter condition. More information on `Filter Configuration`_.

**Syntax**

.. code:: javascript

    collections.deleteOne("<collection_name>", "<filter>", "<options>");

.. list-table:: Input Parameters
    :header-rows: 1

    * - Name
      - Data Type
      - Required
      - Description
    * - *collection_name*
      - [Text](dt-text)
      - *true*
      - Name of the collection to delete the documents from
    * - *filter*
      - [JSON document](dt-json)
      - *true*
      - Filter condition to filter documents by
    * - *options*
      - [JSON document](dt-json)
      - *true* (can be empty with no fields like **{}**)
      - `Arbitrary Options`_ to be passed to the data collection API

**Example**

.. code:: javascript

    let model = lucy.currentModel();
    // or,
    // let model = lucy.model("UserModel");
    let collections = model.collections();
    let filter = {
        {"FirstName": {"$eq": "John"}}
    };
    let options = {};
    
    collections.deleteMany("User", filter, options)
        .then(result => {
            // process result
            runtime.done({});
        })
        .catch(error => {
            runtime.error(error);
        });

### count

Count all matching documents for the given collection & filter condition. More information on `Filter Configuration`_.

**Syntax**

.. code:: javascript

    collections.count("<collection_name>", "<filter>", "<options>");

.. list-table:: Input Parameters
    :header-rows: 1

    * - Name
      - Data Type
      - Required
      - Description
    * - *collection_name*
      - [Text](dt-text)
      - *true*
      - Name of the collection to count the documents from
    * - *filter*
      - [JSON document](dt-json)
      - *true*
      - Filter condition to filter documents by
    * - *options*
      - [JSON document](dt-json)
      - *true* (can be empty with no fields like **{}**)
      - `Arbitrary Options`_ to be passed to the data collection API

.. list-table:: Output
    :header-rows: 1

    * - Data Type
      - Description
    * - [number](dt-numbers)
      - Number of documents that matched the filter condition

**Example**

.. code:: javascript

    let model = lucy.currentModel();
    // or,
    // let model = lucy.model("UserModel");
    let collections = model.collections();
    let filter = {
        {"FirstName": {"$eq": "John"}}
    };
    let options = {};
    
    collections.count("User", filter, options)
        .then(result => {
            // process result
            runtime.done({});
        })
        .catch(error => {
            runtime.error(error);
        });

### aggregate

Perform various aggration on your documents like *sum*, *average*, *min*, *max*, etc for the given collection.

{% hint type="note" %}
    Right now data collections are powered by *MongoDB* in the backend. So, in order to use *Aggregate Pipelines*, checkout the documentation `here <https://docs.mongodb.com/manual/aggregation/>`_ {% endhint %}

**Syntax**

.. code:: javascript

    collections.aggregate("<collection_name>", "<pipeline_stages>", "<options>");

.. list-table:: Input Parameters
    :header-rows: 1

    * - Name
      - Data Type
      - Required
      - Description
    * - *collection_name*
      - [Text](dt-text)
      - *true*
      - Name of the collection to count the documents from
    * - *pipeline_stages*
      - [JSON document](dt-json)
      - *true*
      - Array of pipeline stages to process the data through for aggregation
    * - *options*
      - [JSON document](dt-json)
      - *true* (can be empty with no fields like **{}**)
      - `Arbitrary Options`_ to be passed to the data collection API

.. list-table:: Output
    :header-rows: 1

    * - Data Type
      - Description
    * - [JSON document](dt-json)
      - Aggregation result

**Example**

Here, we need to find the electricity usage of a city. So, we group the data by *City* in our data collection whose *Usage* is more than *50000*, and calculate the *sum* from *Usage* field, and have the aggregation result in *total* field. The result would be,

.. code:: json

####     [
            "_id" : "New York",
            "total": 123456789.0
####         },
            "_id" : "London",
            "total": 12345678.90
####         },
            "_id" : "Mumbai",
            "total": 1234567.890
####         },
            "_id" : "Chennai",
####### #####             "total": 123456.7890

.. code:: javascript

    let model = lucy.currentModel();
    // or,
    // let model = lucy.model("ElectricityMeterModel");
    let collections = model.collections();
    let pipelineStages = [
        { $match: { "Usage": { $gt: 50000 } } },
        { $group: { _id: "$City", total: { $sum: '$Usage' } }},
        { $sort: {total: -1} }
    ];
    let options = {};
    
    collections.aggregate("ElectricityMeterData", pipelineStages, options)
        .then(result => {
            // process result
            runtime.done({});
        })
        .catch(error => {
            runtime.error(error);
        });

### Arbitrary Options

This is provided in order to pass any additional configuration to the backend data collection API.

{% hint type="note" %}
    This may be modified with new features as the backend changes. {% endhint %}

.. list-table:: Available Options
    :header-rows: 1

    * - Name
      - Data Type
      - Required
      - Description
    * - *limit*
      - [number](dt-numbers)
      - *false*
      - Maximum number of documents to return
        
        *default* is **0**
    * - *skip*
      - [number](dt-numbers)
      - *false*
      - Number of documents to skip that match the filter condition

        *default* is **0**
    * - *sort*
      - [number](dt-numbers)
      - *false*
      - Order to sort the matched documents

        **0** for *ascending* & **1** for *descending*

        *default* is **0**

# Settings

The following registry settings are available for data collection feature,

.. list-table:: Settings
    :header-rows: 1

    * - Name
      - Required
      - Description
    * - *MongoDBServer*
      - *true*
      - This is url where your MongoDB instance is running

        **Example:** mongodb://localhost:27017

{% hint style="info" %}

            This setting is used only for MongoDB datastore

{% endhint %}