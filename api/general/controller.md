### Controller

A Controller is a white-label Marionette Object. Its name can be a cause for
confusion, as it actually has nothing to do with the popular MVC architectural pattern.
Instead, it's better to think of the Controller as a base object from which you can build.

Controllers should be used when you have a task that you would like an object to be responsible for,
but none of the other Marionette Classes quite make sense to do it. It's a base object for you to use to
create a new Class altogether.

#### Methods

##### `constructor( [options] )`

The constructor function of Controllers. Calls `initialize`, if it exists. 

##### `initialize( [options] )`

Like every other Backbone Class, this function doesn't exist on the Controller by default. But if
you add an initialize function, either by passing it as an option or by placing it on the Class,
it will be called immediately after the `constructor` each time a new Controller is instantiated.
As its first argument it receives the same options as the constructor.

##### `destroy()`

Destroy the Controller, removing its event listeners and freeing it up for Garbage
Collection.

##### `triggerMethod( eventName )`

Marionette's triggerMethod helper function. It first fires an associated callback for the event, if it exists,
then triggers the event on the object. For more refer to the triggerMethod documentation.

##### `getOption( optionName )`

Marionette's getOption helper function. It is used to get options from this class. First,
it looks for `this.options[optionName]`, and returns it if it exists. If it doesn't exist it checks
`this[optionName]` and returns it if it exists. And if that doesn't exist it returns undefined. For more
refer to the getOption documentation.

##### `extend()`

Backbone's extend method. Used to construct a new Class.

#### Properties

##### `options`

Like all Marionette objects, any options you pass to the constructor are attached to the Controller on the `options`
property.

#### TriggerMethods

Controllers extend Backbone.Events. This gives them access to the Backbone.Events API. The following
are the list of TriggerMethods fired by the Controller Class.
 
##### `destroy`  
Arguments: *The same arguments passed to `close`*

Called when the Controller has been destroyed. The only thing that happens after this
TriggerMethod are the event listeners being unbound.
