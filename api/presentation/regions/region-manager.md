# Region Manager  
Extends from `Marionette.Controller`

xxx

### Methods

#### constructor( [options] )

Basic Controller set up. Calls initialize, if it exists. 

#### initialize()

#### addRegion()

#### addRegions()

#### get()

#### removeRegion()

#### removeRegions()

#### destroyRegions()

#### destroy()

#### destroy()

Destroy the Controller, removing its event listeners and freeing it up for Garbage
Collection.

#### triggerMethod()

### Properties

#### options

#### length

### TriggerMethods

Controllers extend Backbone.Events. This gives them access to the Backbone.Events API. The following
are the list of TriggerMethods fired by the Controller Class.
 
#### before:add:region 
Arguments: `regionName`, `region`

xxx

#### add:region 
Arguments: `regionName`, `region`

xxx

#### before:remove:region 
Arguments: `regionName`, `region`

xxx

#### remove:region 
Arguments: `regionName`, `region`

xxx
