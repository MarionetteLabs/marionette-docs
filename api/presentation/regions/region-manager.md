### Region Manager  
Extends from `Marionette.Controller`

> The Region is a 'background Class'. Background Classes are named because you don't usually
instantiate a Background Class by itself. Instead, other Classes extend from, or include the Background
Class functionality into their own API. Long-story short: you shouldn't ever need to call `new BackgroundClass`.
> The RegionManager API is included as part of Applications and LayoutViews.

Though it is unlikely that you will ever instantiate a `RegionManager` on its own, it can be useful to understand its API to better understand
the internals of the `Application` and `LayoutView`.

#### Methods

##### `constructor( [options] )`

Basic Controller set up. Calls initialize, if it exists. 

##### `initialize()`

##### `addRegion()`

##### `addRegions()`

##### `get()`

##### `removeRegion()`

##### `removeRegions()`

##### `destroyRegions()`

##### `destroy()`

##### `destroy()`

Destroy the Controller, removing its event listeners and freeing it up for Garbage
Collection.

##### `triggerMethod()`

#### Properties

##### `options`

##### `length`

#### TriggerMethods

Controllers extend Backbone.Events. This gives them access to the Backbone.Events API. The following
are the list of TriggerMethods fired by the Controller Class.
 
##### `before:add:region`  
Callback: `onBeforeAddRegion`  
Arguments: `regionName`, `region`

Triggered just before a `region` is added.

##### `add:region`  
Callback: `onAddRegion`  
Arguments: `regionName`, `region`

Triggered just after a `region` is added.

##### `before:remove:region`  
Callback: `onBeforeRemoveRegion`  
Arguments: `regionName`, `region`

Triggered just before a `region` is removed.

##### `remove:region`  
Callback: `onRemoveRegion`  
Arguments: `regionName`, `region`

Triggered just after a `region` is removed.
