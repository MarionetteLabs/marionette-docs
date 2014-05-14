# Region

Views and Regions go hand-in-hand. They both are intended to solve the same goal of displaying
content to your users. But Regions serve as a connector. A View uses its render method to create
a DOM tree, but it isn't attached to anything.

In Marionette you use Regions to attach Views to things. They are typically used for attaching
child views to parents, or views directly to the `document` itself.

### Methods

#### constructor( [options] )

Basic Controller set up. Calls initialize, if it exists. 

#### initialize()

#### ensureEl()

#### getEl()

#### show()

#### attachView()

#### open()

#### reset()

#### destroy()

#### buildRegion()

#### getOption()

#### triggerMethod()

### Properties

#### options

#### el

Required, or an error is thrown.

#### $el

#### currentView

### TriggerMethods

Controllers extend Backbone.Events. This gives them access to the Backbone.Events API. The following
are the list of TriggerMethods fired by the Controller Class.

#### before:show  
Arguments: xxx

xxx

#### show  
Arguments: xxx

xxx

#### before:swap  
Arguments: xxx

xxx

#### swap  
Arguments: xxx

xxx

#### before:destroy  
Arguments: `currentView`

Called just before the current view is destroyed. Passes the about-to-be-destroyed view as an argument.

#### destroy  
Arguments: `currentView`

Called just after the current view is destroyed. Passes the just-destroyed view as an argument.
