# AppRouter  
Extends from `Backbone.Router`

The AppRouter is a slightly enhanced Backbone.Router. All of the knowledge you might have about
the Backbone Router should transfer right over; the feature set is nearly identical. The primary
difference between the two is that the AppRouter places its callbacks on a separate Controller
object to further separate responsibilities.

### Methods

#### constructor( [options] )

#### triggerMethod()

### Properties

#### appRoutes

#### processAppRoutes

#### getOption

### Events

AppRouters extend Backbone.Events. This gives them access to the Backbone.Events API. However,
they do not have the `triggerMethod` function, which makes them unique among the Marionette
Classes. The following are simply triggered events, meaning no associated callback will be
triggered on the AppRouter for the event name.
 
#### destroy  
Arguments: *The same arguments passed to `close`*

Called when the Controller has been destroyed. The only thing that happens after this
TriggerMethod are the event listeners being unbound.
