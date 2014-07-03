# Callbacks

Callbacks provides an means to create a queue of functions to be executed one after another. They are used
internally by the Application and Module classes to power the Initializers and Finalizers.

#### Prototype Methods

##### `add( callback [, context] )`

Add a callback to the list of callbacks, optionally passing the context. The context passed
here takes higher priority than the one passed in through `run`.

All callbacks added after `run` has been called will be executed immediately.

##### `run( [options, context] )`

Execute all of the callbacks. If a context wasn't specified when the callback was added, then the
context supplied here will be used. The options object will be passed as the first argument to each
of the callbacks.

After this method has been called 

##### `reset`

Reset the state of the Callbacks, making it as if `run` had never been called. All previous
callbacks remain; all that changes is that newly added ones will no longer be immediately executed
until `run` is called again.
