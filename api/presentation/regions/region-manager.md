### Region Manager  
Extends from `Marionette.Controller`

> The RegionManager is a 'background Class'. Background Classes are named because one doesn't typically
instantiate a Background Class. Instead, other Classes extend from, or include the Background
Class functionality into their own API.  
> Long-story short: you shouldn't ever need to call `new RegionManager`. The RegionManager API
is included as part of Applications and LayoutViews.

Though it is unlikely that you will ever instantiate or interact directly with a `RegionManager`,
it can be useful to know its API to better understand the internals of the `Application` and `LayoutView`.

#### Methods

##### `constructor( [options] )`

Sets `this.options` and calls the initialize method, if it exists.

##### `initialize( [options] )`

Will be called by the `constructor` if this method exists. Like all Backbone Classes,
this is a function that doesn't exist on the Class by default. You, the developer, are
meant to provide it. It is where you are intended to place startup logic for your Classes.

##### `addRegion( name, definition )`

Add a Region named `name` using the `definition` provided.

##### `addRegions( regionDefinitions, defaults )`

Add multiple regions from the `regionDefinitions` hash. The keys become the names of the regions, and the
values become the `definition` used to create that region. Optionally pass a `defaults` object to use
as the default `definition`.

##### `get( name )`

Returns the region with name `name`.

##### `removeRegion( name )`

Prepare the region named `name` for garbage collection by calling
`empty` on it and removing its event listeners.

##### `removeRegions()`

Set all of the RegionManager's Regions up for garbage collection by calling `empty`
on them and removing their event listeners.

##### `emptyRegions()`

Calls `empty` on each of the RegionManager's Regions.

##### `destroy()`

Prepares the RegionManager for garbage collection by removing all of its Regions and
event listeners by calling `this.stopListening` and `this.off`.

##### `triggerMethod()`

Marionette's triggerMethod helper function. It first fires an associated callback
for the event, if it exists, then triggers the event on the object. For more refer
to the triggerMethod documentation.

#### Properties

##### `options`

Like all Marionette Classes, any options passed into a Region's constructor become
available to that Region on the `options` property.

##### `length`

The number of Regions being managed by the RegionManager.

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
