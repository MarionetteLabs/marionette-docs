### Application

Applications are the entry point into most Marionette Applications. For all but the simplest
of webapps you'll want to instantiate a new Application to act as the hub for the rest of your code.

Applications let you do accomplish three things. Firstly, they provide a place to put start up code for your
app through its Initializers. Secondly, they allow you to group your code into logical sections with the
Module system. Lastly, they give you a way to connect `Views` to the `document` through its Regions.

#### Methods

##### `constructor( [options] )`

The constructor function for the Application. Calls initialize, if it exists. 

##### `addInitializer( fn )`

Adds the function `fn` to the array of 'initializers' for the Application instance. Initializers
are methods that are called, in order, once the application is started.

##### `start()`

Start the application, triggering the Initializers array to be executed in order.

##### `addRegions( regionsHash )`

Adds the hash of Regions to the Application. The keys of the regions hash are the names of the regions
that you're creating. The values in the hash should be query selectors of elements that exist in the DOM.

```js
app.addRegions({
  main:  'main',
  modal: '.modal'
});
```

##### `getRegion( regionName )`

Retrieves the region with the name `regionName` and returns it, if it exists.

##### `removeRegion( regionName )`

Remove the region with the name `regionName`, if it exists.

##### `destroyRegions()`

Destroys all of the regions on the Application instance.

##### `module( moduleName [, moduleDefinition ] )`

Returns a module with `moduleName`. If the module does not exist, it will be created for you. Multiple calls
of the same method will not overwrite a module that has already been created. Nested modules can be accessed
using a space-separated naming format. For instance,

```js
// Access the module 'people', which is a child of the module 'calendar'
app.module('calendar.people');
```

##### `triggerMethod()`

Marionette's triggerMethod helper function. It first fires an associated callback for the event, if it exists,
then triggers the event on the object. For more refer to the triggerMethod documentation.

##### `extend()`

Backbone's extend method. Used to construct a new Class using the Application as the base.

#### Properties

##### `vent`

The `EventAggregator` from the "global" channel. The EventAggregator is simply the Backbone.Events as a
Class. You can treat it as you would any other object that extends from Backbone.Events. The EventAggregator
comes from the Wreqr library, which is included in Marionette. For more I encourage you to read the Wreqr
documentation.

```js
// Listen to an event on the EventAggregator
app.vent.on('some:event', myCallback);

// Trigger the event on the EventAggregator
app.vent.trigger('some:event');
```

##### `commands`

The `Commands` from the "global" channel. Just like `vent`, Commands comes from the Wreqr library and can be used
to dish out orders in a decoupled manner. For more I encourage you to read the Wreqr documentation.

```js

```

##### `reqres`

##### `execute( eventName [, args...] )`

This is a proxy for `Application.prototype.commands.execute`.

```js
// Normally you must write out
this.commands.execute('some:command');

// This proxy saves you some letters
this.execute('some:commands');
```

##### `request( eventName[, args...] )`

This is a proxy for `Application.prototype.reqres.request`.

```js
// The 'long' way to make a request
this.reqres.request('some:request');

// This proxy gives you a shortcut
this.request('some:request');
```

##### `submodules`

#### TriggerMethods

Applications extend Backbone.Events, giving them access to the Backbone.Events API. The following
are the list of TriggerMethods fired by the Controller Class.

##### `before:start`  
Arguments: `options`

Called just before the Application has started. The same options passed to the initializer
as passed onto the start triggerMethod.

##### `start`  
Arguments: `options`

The complement to `before:start`; this is triggered just after the Application starts.

##### `before:add:region`  
Arguments: `regionName`

Called just before a new region is added. The first argument is the name of the new region.

##### `add:region`  
Arguments: `regionName`, `region`

Called just after a new region is added. Passes the region name and region as arguments.

##### `before:remove:region`  
Arguments: `regionName`

Called just before a region is removed. The name of the region is passed as the first argument.

##### `remove:region`  
Arguments: `regionName`, `region`

Called just after a new region is removed. Passes the region name and region as arguments.
