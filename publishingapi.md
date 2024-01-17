


<a name='publishapi'></a>

# Publishing an API

A common use-case for Lucy is to be able to publish an API that can be consumed by some external system such as a native app running on a mobile device.

With Lucy, you can publish RESTful API end points that can be consumed by others.

All APIs in Lucy are published from a model.

Within a model, you can open the API Panel from the sidebar to manage your APIs.

Each API end point you define will map to an [action](actions.md#actions) within your model.

There are 4 major sections in defining an API End Point:

## Action to bind to
Every API will execute an [action](actions.md#actions) in your model.
You need to specify which action will execute for each end point.

{% hint type="note" %}
    Multiple end points can be mapped to the same action.
    This is useful if you want to change the API route but preserve backwards compatibility in some way. {% endhint %}

## Route and Method
You need to specify a route and HTTP method.

The route is the url path for your API.

Note that the first part of the url is fixed as https://<lucyurl>/Lucy/<model>/.

What comes after that is controlled by you.
The path can contain subpaths with / in between.
You can also use placeholders for parameters that can be passed into your action.

Parameters are  given as {paramname}.

As an example:

`/sensors/{sensorid}/value`

When you give this path, your end point can be accessed at http://<lucyurl>/Lucy/<model>/sensors/123/value

And 123 will be passed to the your [action](actions.md#actions) as an input called sensorid.

You also need to specify the HTTP method to use. All the standard methods are available.

Choose an appropriate method based on what your action is doing.

If you are querying data, you should use GET.

Use POST to create a new item.

Use PATCH to update part of an item.

Use PUT to update an entire object.

Use DELETE to remove an object.

{% hint type="note" %}
    The same route can bind to different actions for different HTTP methods. For example, the route /value with a GET can bind to an action that returns a value. The same /value route with a POST an bind to a different action which sets a value. {% endhint %}


## Authentication
By default all API end points you publish in Lucy require authentication.

There are two ways of authenticating requests:

1. API Key

2. OAuth 2

The first mode is the simplest. You just need to add a Authorization: <apikey> header to your request.

You can generate API Keys from the Lucy dashboard or by going to /Apps/System/apikeys in your Lucy account.
Each API Key is associated with a user and will inherit all of that users's permissions.

The second mode is OAuth 2.  [Learn about OAuth 2 Support in Lucy](oauth2)

### Web Hooks

There are some cases where you need to publish an end point that doesn't require authentication.
One example would be to publish a [Web Hook](https://en.wikipedia.org/wiki/Webhook).

Often, integrations to third parties require you to publish a webhook  - an API end point - that can be called by the third party.
In this case, no authentication information will be passed.

You can set the Authentication flag to No Authentication Required to publish an API that doesn't authenticate the user.

{% hint type="note" %}
    If you do publish an end point without authentication, consider using opaque routes that can't be guessed. 
    The Generate Route link in the API Editor will  add a random path in your route for you. {% endhint %}


## Body format
Finally, you need to decide how you will receive inputs from your API end point and how they will map to inputs in your [action](actions.md#actions)

There are several ways in which you can receive your inputs. Which one you choose will depend on how you have defined inputs in your [action](actions.md#actions). Conversely, you may want to structure your action based on what you choose for your API.

{% hint type="note" %}
    None of these body formats apply to API end points that use the GET HTTP method as the HTTP Standard doesn't allow GET requests to have a body. If you want to pass inputs to a GET API, use parameters in your route or query string parameters. See below for how to use query string parameters. {% endhint %}

### JSON

If you choose this body format, the body of the request should be a single JSON dictionary of key/value pairs.
Each key/value pair is sent to the action as an input named after the key.

For example, if your JSON payload is:

```

    {"id":"ts001","value":25.3}

```


Then your [action](actions.md#actions) should have two inputs: id and value.

{% hint type="note" %}
    If your action block is missing some input pins that were specified in the API request, then those parameters will be dropped and will not be available in your action. Conversely, if your action block specifies input pins that were not mapped to any item in the actual request then those will have a null value. {% endhint %}


The JSON dictionary is expected to be flat - that is, no nested objects.

So you cannot use:

```

    {"id":"ts001","value":{"v":25.3,"units":"C"}}

```


If you want to process a complex JSON object, set the body format to Raw Text and process the JSON within your [action](actions.md#actions).

**Required Headers**



```

    POST /Lucy/TempSensor/value
    Authorization: SC:a:19291
    Content-Type: application/json
    {"value":"19,"id":"t01"}

```

### Form Data

If you choose the FormData body format, the body of the request should be either application/x-www-form-urlencoded or 
multipart/form-data

Each key/value pair is sent to the action as an input named after the key.


For example, if your payload is

```

    id=ts001&value=25.3

```


Then your [action](actions.md#actions) should have two inputs: id and value.

**Required Headers**



```

    PUT /Lucy/TempSensor/value
    Authorization: SC:a:19291
    Content-Type: application/x-www-form-urlencoded
    value=19&id=ts01

```


### Raw Text
With this body format, the full payload of the request is available as  UTF-8 text in your action.
It's then up to you to process this in whatever way you want.
Use this if you want to parse a complex JSON structure or some other data format.
The Content-Type can be anything. This is not validated.

The data is available as an input pin called Body.


**Required Headers**



```

    PUT /Lucy/TempSensor/value
    Authorization: SC:a:19291
####     Content-Type: application/json
        "id":"ts01",
        "value":{
            "v":23.3,
            "units":"C"
        },
        "tags":[
            "sensor",
            "temperature",
###### #####             "room01"

```


### Binary
If your input is to be processed as binary data, use Binary as the body format.
This is similar to Raw Text body format except the Body input will be a [binary data object](datatypes.md#binobjects) instead of UTF-8 text.

## Using path variables

As mentioned in the section above on routes you can include variables as part of your path.
Those will be available as input pins to your action, in addition to any inputs provided based on the body format selected.
These variables use {param} syntax.


## Standard Inputs
Apart from inputs that are sent to the action based on the body format selected, there are 4 standard inputs that are always available.
You typically do not need to use them but if do, you can add pins with those names to your action.

The inputs are:



|Query|This will be a [dictionary](datatypes.md#dictionaries) containing all query string parameters that were part of the request|
|Headers|This will be a [dictionary](datatypes.md#dictionaries) containing all HTTP headers that were sent as part of the request.|
|HttpMethod|This will be the name of the HTTP method that was used. This is useful if you want mulitple APIs mapped to a single action.|
|ContentType|This is the value of the Content-Type header that was sent. You can also retrieve this from the Headers [dictionary](datatypes.md#dictionaries) mentioned above, so this is just a convenience since as its the most-accessed header.|
|InstanceKey|If a query string parameter called InstanceKey was passed to the API, that will be available here. If your action was set to run on an instance, then this value will be used to decide which instance to run on.
## Conflicts in input names
Its possible that multiple parameters in the request may map to the same input name when the action is called.
For example, if you have a query string parameter called HttpMethod, that will conflict with the standard HttpMethod parameter that we pass into every request.|
 

In case of conflicts, there is a priority order to resolve it.

First priority is path variables. Anything declared as a path parameter will overwrite anything from a query string or body.

Second priority is body inputs. Any input coming from the body will overwrite any innputs coming from a query string.

Third priority is query string. Any input from a query string that conflicts with one of the standard inputs will overwrite the standard input.


## Publishing APIs for model instances
If your API has to map to an action that runs on an instance of the model, you need some way of obtaining the InstanceKey from the request.

There are three ways this can be done:

1. The caller must pass a query string parameter called InstanceKey to your API
2. Your API must define a route with a {InstanceKey} path variable in it
3. Your API must expect a body format of JSON or FormData and one of the parameters should be InstanceKey

The proper, RESTful way to handle this would be option 2 - a path variable.

As part of your route, use {InstanceKey} in it. And then the caller can put the instance key in there when making a request.

Example of a route:

```

    /sensors/{InstanceKey}/value

```


When the caller makes a request, the path they request to will be

```

    /sensors/213/value

```

The action (if specified as 'Run on Instance') will then run in the context of instance with key=213.

## CORS
All APIs have support for CORS on all http methods.


## Testing your APIs
The API Panel has a section at the end where you can generate code to test your API.

You can choose your language and then copy the code and run it.

Currently, we support cURL - not a language but a command line tool to run requests, and Javascript, using the Javascript fetch api. The javascript code generates a function that tries to extract out all the inputs based on your API definition and the action that its mapped to.