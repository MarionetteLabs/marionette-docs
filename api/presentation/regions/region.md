### Region

> The Region is a 'background Class'. Background Classes are named because you don't usually
instantiate a Background Class by itself. Instead, other Classes extend from, or include the Background
Class functionality into their own API. Long-story short: you shouldn't ever need to call `new BackgroundClass`.
> To create and use Regions you are encouraged to use the Application or LayoutView API.

Views and Regions go hand-in-hand. They are both used to achieve the goal of displaying
content to the viewers of your webapp. But Views and Regions accomplish two distinct tasks to achieve
that goal. As you might already know, Views render the actual content that you would like to display.
But they render that content detached from the rest of the application. Regions serve as the connector
that *attaches* this detached DOM.

Regions are used to link views to both parent views and to the `document` of your page itself.

#### Methods

##### `constructor( [options] )`

Basic Controller set up. Calls initialize, if it exists. 

##### `initialize()`

##### `ensureEl()`

##### `getEl()`

##### `show()`

##### `attachView()`

##### `open()`

##### `reset()`

##### `destroy()`

##### `buildRegion()`

##### `getOption()`

##### `triggerMethod()`

#### Properties

##### `options`

##### `el`

Required, or an error is thrown.

##### `$el`

##### `currentView`

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

After `newView` has replaced the previous view in the Region, then this will be called. This is only called when a swapping
of views occurs; `show` is always called, even if the region was previously empty.

##### `before:empty`  
Callback: `onBeforeEmpty`  
Arguments: `currentView`

Triggered just before the `currentView` in the region is destroyed. Passes the about-to-be-destroyed view as an argument.

##### `empty`  
Callback: `onEmpty`  
Arguments: `currentView`

Triggered just after the `currentView` in the region is destroyed. Passes the just-destroyed view as an argument.
