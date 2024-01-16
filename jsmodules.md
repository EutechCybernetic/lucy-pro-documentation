

# Using Javascript Modules

The [Javascript](blocks.md#es6javascript-ref) block is extremely useful to run complex logic and formulas that are otherwise difficult to express in a visual environment.
The Javascipt engine is ES6 compliant and now has support for referencing external javascipt modules.

With Javascipt modules you can:

* Put your standard code into a separate module that you can reference in your blocks.
* Add suitable 3rd party modules to add functionality to your models.


## Attaching Javascript Modules to Lucy Models
Curently, javascript modules are associated with specific Lucy models.
This means if you want to reference the same module in a different Lucy model, you need to attach it to that model as well.
When you export a Lucy model, any associated Javascript modules get exported as well.

To attach a javascript module to a Lucy model, from the [Model Designer](modeldesigner.md#model-designer) click the menu and choose 'JS Modules'.


<figure><img src=' images/jsmodules.png'></figure>


From the modules panel, you can click the image:: images/attradd.png at the top right to add a new module.

Provide a name for the module. This name will be what you use to reference the module in your code.

{% hint type="note" %}
    Modules are referenced using `require()`  so make sure you choose a "require-friendly" name {% endhint %}

Give a description and then at the bottom select the file or drag it in to upload it.


## Structuring Modules
Javascript has a few ways in which modules can be built and exposed.
For Lucy, the way to do it is by using the  `exports` dictionary in your code.

A sample module:

```

    exports.isValidStatusCode = function(code) {
        if (code < 200) return false;
        if (code > 399) return false;
###         return true;
    exports.MaxTimeout = 25;

```

{% hint type="note" %}
    You can't assign the `exports` dictionary directly. You can only set fields on it.
    So use: {% endhint %}

```

        exports.myFunction = function(){};

```

    and not

```

        exports = {myFunction:function(){} };

```


## Referencing Javascript Modules
You can reference these modules in your |javascript| blocks by using  `require()`.


Using the sample module defined above:

```

    const {isValidStatusCode,MaxTimeout} = require('my-module');
    if (isValidStatusCode()) {runtime.done({ok:1});

```

    

## Referencing 3rd Party Modules
You can make use of 3rd party modules within your models using this technique.
Some examples:

* CryptoJS - provides hashing and other cryptographic primitives that you can use in your models
* Underscore - A popular javascript utility library
* Fuse - Fuzzy text searching
* Datejs - Date parsing/manipulation

You can generally include node modules as well. 

However some restrictions and limitations to keep in mind:

* The module must be available as a single file. Most JS libraries provide a distribution friendly version that is commpiled down to a single file.
* The module can't reference any other external dependencies
* The modules can't reference standard node modules (like `fs`)
* The modules can't make use of standard browser exposed objects like `window` or `document`