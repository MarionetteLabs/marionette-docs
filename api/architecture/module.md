### Modules

#### Prototype Methods

##### `constructor( [options] )`

The constructor function. Sets the properties on the Module and calls `initialize`.

##### `initialize( [options] )`

Will be called by the `constructor` if this method exists. Like all Backbone Classes,
this is a function that either doesn't exist or is a noop by default. You, the developer, are
intended to provide it. It is where you are intended to place startup logic for your Classes.

##### `addInitializer( fn )`

Adds the function `fn` to the array of 'initializers' for the Module instance. Initializers
are methods that are called, in order, once the module is started.

##### `addFinalizer( fn )`

Adds the function `fn` to the array of 'finalizers' for the Module instance. Finalizers are just
like initializers, except that they are called when the module is stopped.

##### `start( [options] )`

Starts the module, passing any `options` to the start triggerMethods and initializers array. This
will also start any submodules that have `startWithParent` set to `true`.

##### `stop( [options] )`

Stops the module, passing any `options` to the stop triggerMethods and finalizers array. This will
also stop all of this module's submodules.

##### `addDefinition( moduleDefinition, customArgs )`

An internal method that does nothing and should be ignored.

##### `extend()`

Backbone's extend method. Used to construct a new Class using the Application as the base.

#### Class Methods

##### `create( app, moduleNames, moduleDefinition )`

This is an internal method used by the Application object to generate new modules. It creates
a series of modules from `moduleNames` that are children of `app`. Pass `moduleDefinition`
to specify properties of the newly created module. 

##### `getClass( moduleDefinition )`

Used by the `create` method to generate a new instance of a Module. If `moduleDefinition` is
an instance of `Marionete.Module` then it will be returned; otherwise it defaults to `Marionette.Module`.

#### Properties

##### `moduleName`

The name of the module. This is specified when you create the Module through the Application's `module`
method.

##### `startWithParent`

A Boolean representing whether or not this Module should start with at the same time the parent starts.
Defaults to true. Pass `false` if you would prefer to manually start the Module.

##### `startWithParentIsConfigured`

An internal property used during module creation to determine if the user has manually set `startWithParent`.
This should be ignored.

##### `submodules`

An internal store of child modules.

##### `app`

A reference to the `Application` instance that the module is attached to.

##### `options`

Like most Marionette Classes, any options passed into a Region's constructor become
available to that Region on the `options` property.

##### `vent`

The `EventAggregator` from the "global" channel. The EventAggregator is simply the Backbone.Events as a
Class. You can treat it as you would any other object that extends from Backbone.Events. The EventAggregator
comes from the Wreqr library, which is included in Marionette. For more I encourage you to read the Wreqr
documentation.

#### TriggerMethods

Modules extend Backbone.Events, giving them access to the Backbone.Events API. The following
are the list of TriggerMethods fired by the Module Class.

##### `before:start`  
Callback: `onBeforeStart`  
Arguments: `options`

Called just before the Module is started. The same options passed to the `initialize` method
is passed onto the before:start triggerMethod.

##### `start`  
Callback: `onStart`  
Arguments: `options`

The complement to `before:start`; this is triggered just after the Application starts.

##### `before:stop`  
Callback: `onBeforeStop`  
Arguments: *none*

Called just before the Module is stopped.

##### `stop`  
Callback: `onStop`  
Arguments: *none*

The complement to `before:stop`; this is triggered just after the Module is stopped.
