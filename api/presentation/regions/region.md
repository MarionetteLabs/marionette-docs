### Region

> The Region is a 'background Class'. Background Classes are named because one doesn't typically
instantiate a Background Class. Instead, other Classes extend from, or include the Background
Class functionality into their own API. Long-story short: you shouldn't ever need to call `new Region`.
> Instead, to create and use Regions you are encouraged to use the Application or LayoutView API.

Views and Regions go hand-in-hand. They are both used to achieve the goal of presenting
content to the viewers of your webapp. But Views and Regions accomplish two distinct tasks to achieve
that goal.

As you might already know, Views render the actual content that you would like to display.
But not all Views render content that is attached to the `document`. These views render a detached DOM
tree, that isn't visible to the user. This creates a new responsibility: attaching that detached tree
to another tree. This is what Regions are for: they serve as a connector between DOM trees.

In other words, Regions are used to attach views to parent views and also to the `document` of your page
itself.

#### Prototype Methods

Prototype methods are those methods which are available on each instance of the Region.

##### `constructor( [options] )`

The constructor method for the Region. It sets the `options`, `el`, and `$el` properties
on the region. It also calls `initialize`, if it exists.

##### `initialize( [options] )`

Will be called by the `constructor` if this method exists. Like all Backbone Classes,
this is a function that doesn't exist on the Class by default. You, the developer, are
meant to provide it. It is where you are intended to place startup logic for your Classes.

##### `getEl( el )`

Returns the jQuery Object of `el`. Do note that it is not recommended that you override
this method because it is ignored in certain circumstances.

##### `show( newView [, options] )`

Shows `newView` inside the region if it isn't already shown. The previous view, if one exists,
will be destroyed in this process. The `show` methods fires the show and swap triggerMethods.

You can modify the behavior of `show` by passing in an options object.

`preventDestroy`  
Pass this as `true` to prevent the destruction of the old view. This is not recommended, as Views
are intended to be throwaway objects in Marionette. You are encouraged to only use this option
if the View you are rendering is a render-heavy view, such as a large chart or graphic.

`forceShow`  
By default passing the same view to `show` will be a noop; your view will not be rendered, and no
events will be fired. Pass `true` for this option to cause the entire show process to happen again,
including events and the re-rendering of your view.

##### `attachView( view )`

Associate a new view with the region by setting the region's value of `currentView`. This will not call render,
show, or fire any events.

##### `attachHtml( view )`

This method determines how the view's html is attached to the Region's element. The default
method is using append. You can override this if you would like to, for instance, specify that
the view's element fade in to view.

Note that the creation of an animated region is a more involved process than just this. For more,
refer to the guide on animated regions.

##### `reset()`

Reset the region by calling `empty`, which destroys its view and clears its content. It then deletes
the cached `$el` property. Finally it sets `this.el` to the value of the selector string of the old
element.

This prepares the Region to be 're-initialized' with a new element based on the old selector
string, and is used by the LayoutView when it re-renders itself.

##### `empty()`

Empty calls `destroy` on the `currentView`. This has the consequence of clearing the contents
of the Region.

##### `getOption()`

Marionette's getOption helper function. It is used to get options from this class. First,
it looks for `this.options[optionName]`, and returns it if it exists. If it doesn't exist it checks
`this[optionName]` and returns it if it exists. And if that doesn't exist it returns undefined. For more
refer to the getOption documentation.

##### `triggerMethod()`

Marionette's triggerMethod helper function. It first fires an associated callback
for the event, if it exists, then triggers the event on the object. For more refer
to the triggerMethod documentation.

#### Class Methods

Class Methods are available from the Region Class object.

##### `buildRegion( regionConfig, defaultRegionClass )`

Returns a new Region from the `regionConfig` object. This is used by the RegionManager to
create a new Region instance.

#### Properties

##### `options`

Like all Marionette Classes, any options passed into a Region's constructor become
available to that Region on the `options` property.

##### `el`

Like Views, Regions have an associated element. The difference between the two, though, is that
a Region's `el` must exist at the time that the Region is created, otherwise an error will be thrown.
This is because the role of a Region is to manage what view is being shown in an already-existing
element. Regions do not create new elements.

Also like Views, valid values for el are a query selector string, a DOM node, or a jQuery object.

##### `$el`

A cached version of the jQuery object for the Region's element.

##### `currentView`

The current view that is being shown in the region.

#### TriggerMethods

Controllers extend Backbone.Events. This gives them access to the Backbone.Events API. The following
are the list of TriggerMethods fired by the Controller Class.

##### `before:show`  
Callback: `onBeforeShow`  
Arguments: `view`  

Called just before the Region displays `view` in itself.

##### `show`  
Callback: `onShow`  
Arguments: `view`

Called just after the Region displays `view` in itself.

##### `before:swap`  
Callback: `onBeforeSwap`  
Arguments: `newView`

Unlike the `show` triggerMethod this is only triggered when the Region is *already* showing a
view, and has been told to show `newView`. It is called before the swap happens.

##### `swap`  
Callback: `onSwap`  
Arguments: `newView`

After `newView` has replaced the previous view in the Region, then this will be called. Unlike the `show` triggerMethod, this is only called when a swapping
of views occurs.

##### `before:empty`  
Callback: `onBeforeEmpty`  
Arguments: `currentView`

Triggered just before the `currentView` in the region is destroyed. Passes the about-to-be-destroyed view as an argument.

##### `empty`  
Callback: `onEmpty`  
Arguments: `currentView`

Triggered just after the `currentView` in the region is destroyed. Passes the just-destroyed view as an argument.
