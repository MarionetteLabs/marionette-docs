### AppRouter  
Extends from `Backbone.Router`

The AppRouter is an enhanced Backbone.Router. All of the knowledge you might have about
the Backbone Router should transfer right over; the feature set is nearly identical. The primary
difference between the two is that the AppRouter allows you to place callbacks on a separate object
– a Controller – whereas a Backbone Router can only have callbacks that exist on the Router itself.

#### Prototype Methods

##### `constructor( [options] )`

Sets the `options` property and registers the routes specified in the `appRoutes` hash using `processAppRoutes`.

##### `processAppRoutes( controller, appRoutes )`

An internal method that gets the methods from `controller` based on the `appRoutes` hash, then links
it up to the `Backbone.history` object.

##### `getOption( optionName )`

Marionette's getOption helper function. It is used to get options from this class. First,
it looks for `this.options[optionName]`, and returns it if it exists. If it doesn't exist it checks
`this[optionName]` and returns it if it exists. And if that doesn't exist it returns undefined. For more
refer to the getOption documentation.

#### Properties

##### `controller`

The Controller for the routes of this AppRouter. This object is where the method names in the `appRoutes` hash
should exist.

##### `appRoutes`

Similar to the `routes` hash, but references routes on the Controller for this router. The keys of the hash
are the routes to be matched; the values of the hash are strings that must be function names on the
Controller.

#### Events

AppRouters extend Backbone.Events. This gives them access to the Backbone.Events API. However,
they do not have the `triggerMethod` function, which makes them unique among the Marionette
Classes. The following are simply triggered events, meaning no associated callback will be
triggered on the AppRouter for the event name.
 
##### `route:[name]`  
Callback: *None*  
Arguments: *params*

Triggered by the router when when the `[name]` route is matched.

##### `route`  
Callback: onRoute
Arguments: `router`, `route`, *params*

Triggered by the router when whenever any route is matched.
