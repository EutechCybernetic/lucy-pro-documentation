


<a name='designpatterns'></a>

# Design Patterns
So lets talk about the various design patterns that are commonly used for deploying a solution on top of Lucy. These are patterns that we see commonly and are useful enough that you will probably come across them too and may want to make use of them for your solution.

## Object Extension Pattern
A common task you often see is the need to take an existing object (either a model or some other iviva object) and extend it by giving it extra attributes and building extra logic on top of it.

An example of an extension would be:
- Extending a location to make it a facility that is bookable.
- Extending an employee model to add extra information related to his access card details

TODO: fill in the rest


## Object Mapping Pattern
TODO: Used to bind 2 objects together in a relationship.

(Binding a location to a sensor)


## Coordinator Pattern
TODO: Using a base model to define common methods and then dispatch the work to the relevant model instance
(Like a LightControl model or something)


## Managing lists of items
TODO: Defining a child model that holds the items of the list with a reference to the parent

## External Connector Pattern
TODO: Connector raises events, models listen and publish.
Use of action names sent down to the connector to allow it to call back to a specific action with details.
Use of a temporary channel name or event name to return 'results' from the connector.