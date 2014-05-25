### AppRouter  
Extends from `Backbone.Router`

The AppRouter is an enhanced Backbone.Router. All of the knowledge you might have about
the Backbone Router should transfer right over; the feature set is nearly identical. The primary
difference between the two is that the AppRouter places its callbacks on a separate object to
further enforce separation of concerns.

#### Methods

##### `constructor( [options] )`

##### `triggerMethod()`

#### Properties

##### `appRoutes`

##### `processAppRoutes`

##### `getOption`

#### Events

AppRouters extend Backbone.Events. This gives them access to the Backbone.Events API. However,
they do not have the `triggerMethod` function, which makes them unique among the Marionette
Classes. The following are simply triggered events, meaning no associated callback will be
triggered on the AppRouter for the event name.
 
##### `route:[name]`  
Callback: *None*  
Arguments: *params*

Triggered by the router when when the `[name]` route is matched.

##### `route:[name]`  
Callback: *None*  
Arguments: `route`, *params*

Triggered by the router when whenever any route is matched.
