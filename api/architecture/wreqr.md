### Wreqr

Wreqr is a system of communication that adds a semantic layer on top of the well-established
pub-sub messaging pattern. It does this by supplying you with three messaging systems that can
be used to convey more meaning than simply emitting events.

### EventAggregator

The Event Aggregator should be familiar to anyone who has used Backbone: it's just
the Backbone.Events object in Class Form. Backbone.Events, and consequently the EventAggregator,
is a pub-sub in its traditional form.

The EventAggregator is literally a Class form of Backbone.Events. Consequently, it's API is identical. Please
refer to [Backbone.Events documentation](http://backbonejs.org/#Events).

#### `extend`

The extend method from Backbone. Used to add functionality to the EventAggregator Class.

### Commands

Commands is the second messaging protocol of Wreqr. It is used to coordinate actions between objects in a decoupled
manner.

Unlike the EventAggregator, information is not returned from the executed Command, whereas Events pass information along about
the event that has occurred.

#### Prototype Methods

##### `execute( commandName [, args...] )`

Order a command to be completed. Optionally pass arguments to send along to the callback.

##### `setHandler( commandName, callback [, context] )`

Register a handler for `commandName` on this object. `callback` will be executed whenever the command is run. Optionally
pass a `context` for the callback, defaulting to `this`.

##### `setHandlers( handlersHash )`

Attach multiple handlers to the instance of Commands at one time.

##### `removeHandler( commandName )`

Remove the handler for `commandName`.

##### `removeAllHandlers()`

Remove every handler from the instance of Commands.

#### `extend`

The extend method from Backbone. Used to add functionality to the Commands Class.

### RequestResponse

RequestResponse is the third and final messaging protocol of Wreqr. It is used to send information between two objects
in a decoupled manner.

#### Prototype Methods

##### `request( requestName [, args...] )`

Make a request for `requestName`. Optionally pass arguments to send along to the callback.

##### `setHandler( requestName, callback [, context] )`

Register a handler for `requestName` on this object. `callback` will be executed whenever the command is run. Optionally
pass a `context` for the callback, defaulting to `this`.

##### `setHandlers( handlersHash )`

Attach multiple handlers to the instance of RequestResponse at one time.

##### `removeHandler( requestName )`

Remove the handler for `requestName`.

##### `removeAllHandlers()`

Remove every handler from the instance of RequestResponse.

#### `extend`

The extend method from Backbone. Used to add functionality to the RequestResponse Class.

### Radio

Radio is an API that allows you to work with Channels, which function as explicit namespaces for your Wreqr events.

#### `channel( channelName )`

Get a handle of a channel by its name. If the Channel doesn't exist, it will be created for you. Otherwise, it
returns the already-created Channel.

#### `vent`

A 'top-level' API for accessing the `vent` object of any Channel. Pass the name of the Channel as the first argument to run
the method on the specified Channel.

```js
// Trigger an item added event on the groceries channel
Wreqr.Radio.vent.trigger('groceries', 'add:item', myItem);
```

#### `reqres`

A 'top-level' API for accessing the `reqres` object of any Channel. Execute any method of RequestResponse, passing
the name of the Channel as the first argument, to run that method on the specified Channel. This can be used to run methods
on a Channel without keeping a handle on that Channel.

```js
// Request the groceryList from the groceries channel
Wreqr.Radio.reqres.request('groceries', 'groceryList');
```

#### `commands`

Similar to the top-level API for the EventAggregator and RequestResponse above. Commands is used to access the Commands instance on any
Channel without keeping a reference to the Channel. Pass the name of the Channel as the first argument to run
the method on the specified Channel.

```js
// Set a Commands handler on the groceries Channel
Wreqr.Radio.commands.setHandler('groceries', 'sort:groceryList', sortGroceryList);
```

### Channels

Channels are objects with an instance of Wreqr.EventAggregator, Wreqr.RequestResponse, and Wreqr.Commands on it. They
are used to namespace your application's events.

#### `vent`

An instance of `Wreqr.EventAggregator`.

#### `reqres`

An instance of `Wreqr.RequestResponse`

#### `commands`

An instance of `Wreqr.Commands`
