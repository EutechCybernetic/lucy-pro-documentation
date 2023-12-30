

[trends:](trends:)

======
# Trends

Trends feature allows you to record a *data point* tied to a *specific timestamp*. This later provide the ability to extract trends from data points that were recorded over time. This techincally called as a `Time series <https://en.wikipedia.org/wiki/Time_series>`_ data.

An example of a trend/timeseries would be recording energy usage of an equipment in a location. The *data point* would primarily have a *value*, *timestamp* and additional tags/metadata like *Location*, *Equipment ID*, *Equipment Type* and so on. Once you've gathered enough data points concering multiple equipments in multiple locations, you could extract trends like,

1. Energy usage per day/week/month/year
2. Energy usage per location
3. Energy usage by Equiptment Type
4. Energy usage by Equipment ID

Trends can be stored on a traditional SQL database like MySQL, Postgres SQL, SQL Server and so on. But, as data grows over time, it becomes hard to manage and really slow to query. That is where Lucy harnesses the power of timeseries databases like Cassandra, InfluxDB, TimescaleDB and so on, that are designed from ground up to handle this kind of data. Right now trends are backed by `InfluxDB <https://www.influxdata.com/>`_ and other backends are either being considered or under development.

# Working with Trends

You can work with trends through the following interfaces,

1. `Lucy Blocks`_
2. `Javascript API`_

## Lucy Blocks

These blocks are your everyday Lucy blocks, that enable you to work with the trends visually. The following blocks are provided for you and we will go through each of them in detail,

1. `Add Point`_
2. `Query Points`_

### Add Point

This blocks allows you to record a data point for the given trend.

.. list-table:: Input Pins
    :header-rows: 1

    * - Name
      - Data Type
      - Required
      - Description
    * - *Trend Name*
      - [Text](dt-text)
      - *true*
      - Name of the trend you are capturing like *energy* or *temperature*
    * - *Value*
      - [number](dt-numbers)
      - *true*
      - Value of the data point you are capturing like *12.07* or *100*
    * - *Timestamp*
      - [Datetime](dt-datetimes)
      - *false* (*default*: current time)
      - Records the time when the data point was captured
    * - *Tag List*
      - [JSON Document](dt-json)
      - *false*
      - Additional metadata associated with the datapoint like *Location*, *Equipment ID*, *Equipment Type*

The following steps illustrate how you can add a point,

1. From the blocks menu, choose **Time Series** -> **Add Point** & add it to your lucy action
2. Pass values to the input pins. For *Tag List* input pin, you can either use [Make JSON Block](jsonobject-ref), [Javascript Block](javascript-ref) or [ES6 Javascript Block](es6javascript-ref) to construct your **JSON document** and pass it as value.

On successful insert, you should get an output of **1** from the *All Output* pin.

**Illustration**

<figure><img src=' images/trends/blocks/add-1-point-block.png'></figure>

### Query Points

This blocks allows you to query data points for the given trend.

.. list-table:: Input Pins
    :header-rows: 1

    * - Name
      - Data Type
      - Required
      - Description
    * - *Trend Name*
      - [Text](dt-text)
      - *true*
      - Name of the trend you want to query like *energy* or *temperature*
    * - *Bucket Type*
      - [text](dt-text)
      - *false*
      - Time buckets to group data points by.

        Available buckets - Hour, Day, Week, Month, Year
    * - *Aggregation Type*
      - [text](dt-text)
      - *false*
      - Aggregation to be performed on the data

        Available aggregation - Sum, Average, Max, Min
    * - *From*
      - [Datetime](dt-datetimes)
      - *false*
      - Timestamp from which data points should be gathered
    * - *To*
      - [Datetime](dt-datetimes)
      - *false*
      - Timestamp until which data points should be gathered
    * - *Tag List*
      - [JSON Document](dt-json)
      - *false*
      - Additional metadata associated with the datapoint like *Location*, *Equipment ID*, *Equipment Type*. This will be used to filter out the data points
    * - *Offset*
      - [number](dt-numbers)
      - *false* (*default*: 0)
      - Number of data points to skip
    * - *Descending*
      - [number](dt-numbers)
      - *false* (*default*: 0)
      - Sort order for the data points

        **0** for *ascending* & **1** for *descending*

        *default* is **0**
    * - *Limit*
      - [number](dt-numbers)
      - *false* (*default*: 50)
      - Maximum number of data points to return

The following steps illustrate how you can add a point,

1. From the blocks menu, choose **Time Series** -> **Query Points** & add it to your lucy action
2. Pass values to the input pins. For *Tag List* input pin, you can either use [Make JSON Block](jsonobject-ref), [Javascript Block](javascript-ref) or [ES6 Javascript Block](es6javascript-ref) to construct your **JSON document** and pass it as value.

On successful insert, you should get all data points in the *All Output* pin.

**Illustration**

<figure><img src=' images/trends/blocks/query-points-block.png'></figure>

## Javascript API

1. `addPoint`_
2. `addPointSync`_
3. `addPoints`_
4. `addPointsSync`_
5. `queryPoints`_

### addPoint

Insert one data point at a time.

{% hint style="info" %}

    This API return a Javascript Promise, you can checkout more details about it & how to use them [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises).

{% endhint %}

**Syntax**

.. code:: javascript

    let trends = lucy.trends();
    trends.addPoint("<trend_name>", "<value>", "<timestamp>", "<tags>", "<options>");

.. list-table:: Input Parameters
    :header-rows: 1

    * - Name
      - Data Type
      - Required
      - Description
    * - *trend_name*
      - [Text](dt-text)
      - *true*
      - Name of the trend you are capturing like *energy* or *temperature*
    * - *value*
      - [number](dt-numbers)
      - *true*
      - Value of the data point you are capturing like *12.07* or *100*
    * - *timestamp*
      - [Datetime](dt-datetimes)
      - *true*
      - Records the time when the data point was captured
    * - *tags*
      - [JSON Document](dt-json)
      - *true*
      - Additional metadata associated with the datapoint like *Location*, *Equipment ID*, *Equipment Type*
    * - *options*
      - [JSON document](dt-json)
      - *true* (can be empty with no fields like **{}**)
      - `Arbitrary Options`_ to be passed to the trends API

**Example**

.. code:: javascript

    let trend = 'energy';
    let value = 120;
    let timestamp = new Date();
    let tags = {
        'Location': 1,
        'ID': 'E001'
    };

    let trends = lucy.trends();

    trends.addPoint(trend, value, timestamp, tags, {})
        .then(result => {
            runtime.done({});
        })
        .catch(err => {
            runtime.error(err);
        });

### addPointSync

Insert one data point at a time. This is similar to `addPoint`_, except that this API doesn't return a promise.

**Syntax**

.. code:: javascript

    let trends = lucy.trends();
    trends.addPoint("<trend_name>", "<value>", "<timestamp>", "<tags>", "<options>");

.. list-table:: Input Parameters
    :header-rows: 1

    * - Name
      - Data Type
      - Required
      - Description
    * - *trend_name*
      - [Text](dt-text)
      - *true*
      - Name of the trend you are capturing like *energy* or *temperature*
    * - *value*
      - [number](dt-numbers)
      - *true*
      - Value of the data point you are capturing like *12.07* or *100*
    * - *timestamp*
      - [Datetime](dt-datetimes)
      - *true*
      - Records the time when the data point was captured
    * - *tags*
      - [JSON Document](dt-json)
      - *true*
      - Additional metadata associated with the datapoint like *Location*, *Equipment ID*, *Equipment Type*
    * - *options*
      - [JSON document](dt-json)
      - *true* (can be empty with no fields like **{}**)
      - `Arbitrary Options`_ to be passed to the trends API

**Example**

.. code:: javascript

    let trend = 'energy';
    let value = 120;
    let timestamp = new Date();
    let tags = {
        'Location': 1,
        'ID': 'E001'
    };

    let trends = lucy.trends();

    trends.addPoint(trend, value, timestamp, tags, {})
    
    runtime.done({});

### addPoints

Insert multiple data point at a time.

{% hint style="info" %}

    This API return a Javascript Promise, you can checkout more details about it & how to use them [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises).

{% endhint %}

**Syntax**

.. code:: javascript

    let trends = lucy.trends();
    trends.addPoints("<points>", "<options>");

.. list-table:: Input Parameters
    :header-rows: 1

    * - Name
      - Data Type
      - Required
      - Description
    * - *points*
      - [JSON Documents](dt-json)
      - *true*
      - Array of JSON documents comprising of trend points
      
        Refer to **Trend Point** structure below
    * - *options*
      - [JSON document](dt-json)
      - *true* (can be empty with no fields like **{}**)
      - `Arbitrary Options`_ to be passed to the trends API

**Trend Point**

.. code:: json

    {
      trend: "<trend_name>",
      value: <value>,
      timestamp: <timestamp>,
#####       tags: <tags>

**Example**

.. code:: javascript

    let trends = lucy.trends();
    let points = [];

    for(let i = 0; i < 100; i++) {
        points.push({
            trend: 'energy',
            value: i,
            timestamp: new Date(),
            tags: {
                Location: '1',
#####                 ID: 'E00' + i
#####         });

    trends.addPoints(points, {})
        .then(result => runtime.done({}))
        .catch(err => {
            runtime.error(err);
        });

### addPointsSync

Insert multiple data point at a time. This is similar to `addPoints`_, except that this API doesn't return a promise.

**Syntax**

.. code:: javascript

    let trends = lucy.trends();
    trends.addPointsSync("<points>", "<options>");

.. list-table:: Input Parameters
    :header-rows: 1

    * - Name
      - Data Type
      - Required
      - Description
    * - *points*
      - [JSON Documents](dt-json)
      - *true*
      - Array of JSON documents comprising of trend points
      
        Refer to **Trend Point** structure below
    * - *options*
      - [JSON document](dt-json)
      - *true* (can be empty with no fields like **{}**)
      - `Arbitrary Options`_ to be passed to the trends API

**Trend Point**

.. code:: json

    {
      trend: "<trend_name>",
      value: <value>,
      timestamp: <timestamp>,
#####       tags: <tags>

**Example**

.. code:: javascript

    let trends = lucy.trends();
    let points = [];

    for(let i = 0; i < 100; i++) {
        points.push({
            trend: 'energy',
            value: i,
            timestamp: new Date(),
            tags: {
                Location: '1',
#####                 ID: 'E00' + i
#####         });

    trends.addPoints(points, {})
    
    runtime.done(outputs)

### queryPoints

Query multiple data points for a given trend.

{% hint style="info" %}

    This API return a Javascript Promise, you can checkout more details about it & how to use them [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises).

{% endhint %}

**Syntax**

.. code:: javascript

    let trends = lucy.trends();
    trends.queryPoints("<trend_name>", "<from>", "<to>", "<tags>", "<bucketType>", "<aggregationType>", "<options>");

.. list-table:: Input Pins
    :header-rows: 1

    * - Name
      - Data Type
      - Required
      - Description
    * - *trend_name*
      - [Text](dt-text)
      - *true*
      - Name of the trend you want to query like *energy* or *temperature*
    * - *from*
      - [Datetime](dt-datetimes)
      - *true*
      - Timestamp from which data points should be gathered
    * - *to*
      - [Datetime](dt-datetimes)
      - *true*
      - Timestamp until which data points should be gathered
    * - *bucket_type*
      - [text](dt-text)
      - *true*
      - Time buckets to group data points by.

        Available buckets - hour, day, week, month, year
    * - *aggregation_type*
      - [text](dt-text)
      - *true*
      - Aggregation to be performed on the data

        Available aggregation - sum, average, max, min
    * - *tags*
      - [JSON Document](dt-json)
      - *false*
      - Additional metadata associated with the datapoint like *Location*, *Equipment ID*, *Equipment Type*. This will be used to filter out the data points
    * - *options*
      - [JSON document](dt-json)
      - *true* (can be empty with no fields like **{}**)
      - `Arbitrary Options`_ to be passed to the trends API

**Example**

.. code:: javascript

    let trends = lucy.trends();
    let tags = {
      'Location': 1
    };
    let fr = new Date();
    fr.setUTCDate(1);
    let to = new Date();
    to.setUTCDate(30);

    trends.queryPoints('energy', fr, to, tags, 'day', 'sum' {})
        .then(result => {
          // process results
          runtime.done({});
        })
        .catch(err => {
            runtime.error(err);
        });

### Arbitrary Options

This is provided in order to pass any additional configuration to the backend trends API.

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
      - Maximum number of trends to return
        
        *default* is **0**
    * - *offset*
      - [number](dt-numbers)
      - *false*
      - Number of trends to skip

        *default* is **0**
    * - *sort*
      - [number](dt-numbers)
      - *false*
      - Order to sort the data points

        **0** for *ascending* & **1** for *descending*

        *default* is **0**

# Settings

The following registry settings are available for trends feature,

.. list-table:: Settings
    :header-rows: 1

    * - Name
      - Required
      - Description
    * - *LucyEngine.TimeSeries.DataStore*
      - *false*
      - Backend datastore to use for storing trend data
        
        *default* is **influxdb**
    * - *LucyEngine.TimeSeries.FlushInterval*
      - *false*
      - This says the interval at whichc the incoming trend data should be flushed into the datastore. This    can be tuned based on the rate at which trend points are being added. If large of number data is       added in a short period of time, then you can reduce this interval, to avoid bulk flushing in the      backend. 
      
        For example, if you get **5000 data points** every **5 seconds**, then you could set this value to say **1000** (*milliseconds*), to avoid flushing data in bulk.

        For example, if you get only **10 data points** every **1 second**, then you could set this value to say **10000** (*milliseconds*), to avoid flushing too little data.

        *default* is **5000** (*milliseconds*)
    * - *LucyEngine.TimeSeries.MaxFlushThreshold*
      - *false*
      - This says the *maximum* amount of trend points we can hold in memory, before flushing them into the    datastore. This can be tuned based on the **LucyEngine.TimeSeries.FlushInterval** setting. This is useful in cases where we get large data too often, but flush later.

        For example, if you get **1000 data points** every **1 second**, but **LucyEngine.TimeSeries.FlushInterval** is set to **30000** (*milliseconds*), then you could set this to **1000**, to avoid flushing large data over longer time.

        *default* is **255**
    * - *LucyEngine.TimeSeries.MinFlushThreshold*
      - *false*
      - This says the *minimum* amount of trend points we need to have in memory, before flushing them into    the datastore. This can be tuned based on the **LucyEngine.TimeSeries.FlushInterval** setting. This is useful in cases where we get little data, but flush sooner.

        For example, if you get **10 data points** every **1 second**, but **LucyEngine.TimeSeries.FlushInterval** is set to **100** (*milliseconds*), then you could set this to **100**, to avoid flushing little data too often.

        *default* is **10**
    * - *LucyEngine.TimeSeries.InfluxUrl*
      - *false*
      - This is url where your InfluxDB instance is running

        *default* is **http://localhost:8086**

{% hint style="info" %}

            This setting is used only for InfluxDB datastore

{% endhint %}