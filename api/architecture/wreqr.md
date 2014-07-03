### Wreqr

Wreqr is a communication system that adds a semantic layer on top of the well-established
pub-sub messaging pattern. It does this by supplying you with three messaging systems that can
be used to convey more meaning than simply emitting events.

### EventAggregator

The Event Aggregator should be familiar to anyone who has used Backbone: it's just
the Backbone.Events object in Class Form. Backbone.Events, and consequently the EventAggregator,
is a pub-sub in its traditional form.

#### Prototype Methods

##### `on()`

##### `once()`

##### `off()`

##### `listenTo()`

##### `listenToOnce()`

##### `stopListening()`

### Commands

Commands is different from the EventAggregator in two key ways. The first way is that it carries intent. 

#### Prototype Methods

##### `execute( commandName [, args...] )`

Order a command to be completed. Optionally pass arguments to send along to the callback.

##### `setHandler( commandName, callback [, context] )`

Register a handler for `commandName` on this object. `callback` will be executed whenever the command is run. Optionally
pass a `context` for the callback, defaulting to `this`.

##### `removeHandler( commandName )`

Remove the handler for `commandName`.

##### `removeAllHandlers()`

Remove every handler from the instance of Commands.

### Requests

##### `request( requestName [, args...] )`

Make a request for `requestName`. Optionally pass arguments to send along to the callback.

##### `respond( requestName, callback [, context] )`

Register a handler for `requestName` on this object. `callback` will be executed whenever the request is made. Optionally
pass a `context` for the callback, defaulting to `this`.

##### `respondOnce( requestName, callback [, context] )`

Register a handler for `requestName` that will only be called a single time.

##### `stopResponding( [requestName] )`

If `requestName` is passed then this method will remove that response. Otherwise, all responses are removed from the object.
