# Controller

A Controller is a white-label Marionette Object. Its name can be a cause for
confusion, as it actually has nothing to do with the popular MVC architectural pattern.

You should use a Controller to handle tasks that you may want to abstract from Views or Models.

### Methods

#### constructor( [options] )

Basic Controller set up. Calls initialize, if it exists. 

#### initialize()

#### destroy()

Destroy the Controller, removing its event listeners and freeing it up for Garbage
Collection.

#### triggerMethod()

#### getOption()

#### extend()

### Properties

#### options

### TriggerMethods

Controllers extend Backbone.Events. This gives them access to the Backbone.Events API. The following
are the list of TriggerMethods fired by the Controller Class.
 
#### destroy  
Arguments: *The same arguments passed to `close`*

Called when the Controller has been destroyed. The only thing that happens after this
TriggerMethod are the event listeners being unbound.
