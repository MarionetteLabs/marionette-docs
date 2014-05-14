# Application

Applications are the entryway into most Marionette Applications. For all but the simplest
of applications you'll want to instantiate a new Application to contain the rest of your code.

### Methods

#### constructor( [options] )

Basic Application set up. Calls initialize, if it exists. 

#### execute()

#### request()

#### addInitializer()

#### start()

#### addRegions()

#### getRegion()

#### removeRegion()

#### destroyRegions()

#### module()

#### triggerMethod()

#### extend()

### Properties

#### vent

#### commands

#### reqres

#### submodules

### TriggerMethods

Applications extend Backbone.Events. This gives them access to the Backbone.Events API. The following
are the list of TriggerMethods fired by the Controller Class.

#### before:start  
Arguments: `options`

Called just before the Application has started. The same options passed to the initializer
as passed onto the start triggerMethod.

#### start  
Arguments: `options`

The complement to `before:start`; this is triggered just after the Application starts.

#### before:add:region  
Arguments: `regionName`

Called just before a new region is added. The first argument is the name of the new region.

#### add:region  
Arguments: `regionName`, `region`

Called just after a new region is added. Passes the region name and region as arguments.

#### before:remove:region
Arguments: `regionName`

Called just before a region is removed. The name of the region is passed as the first argument.

#### remove:region  
Arguments: `regionName`, `region`

Called just after a new region is removed. Passes the region name and region as arguments.
