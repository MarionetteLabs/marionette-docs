# Helpers

These methods are used internally throughout Marionette.

##### `extend( prototypeProps [, staticProps ] )`

A reference to `Backbone.Model.Extend`.

##### `getOption( target, optionName )`

Obtain `optionName` from the `target`, if it exists. First, it looks for `target.options[optionName]`. If
that doesn't exist it looks for `target[optionName]`. It returns the first that it finds, returning `undefined`
if nothing is found.

##### `proxyGetOption( optionName )`

Execute `getOption` with `this` as the target. Used on the prototypes
of the Marionette Classes.

##### `normalizeMethods( hash )`

Converts a hash that maps strings to method names to a map of strings to the actual methods on `this`.
If the method does not exist on then that key-value pair will be dropped. The normalized hash is
returned.

To give an example, the following hash:

```js
var hash = {
  'some:event': 'myCallback'
};
```

would be converted to:

```js
var hash = {
  'some:event': this.myCallback
};
```

##### `normalizeUIKeys( hash, ui )`

Used internally by Views to parse the `@ui` syntax in a hash of DOM events. It works by replacing the `@ui`
reference with the corresponding element from the View's `ui` hash. For instance,

```js
var hash = {
  'click @ui.myButton': 'onClickMyButton'
};
```

would be transformed to reference the element specified as `view.ui.myButton`.

The normalized hash is returned by the method.

##### `actAsCollection( object, listProperty )`

Mixes in a number of Underscore methods for working with Collections to the `object`, binding
their context to the `listProperty`. This is similar to how Backbone.Collection has Underscore
methods on the prototype that execute with the `models` property of the Collection as the context.

##### `monitorDomRefresh( view )`

Manages the `onDomRefresh` triggerMethod for the view. This special triggerMethod is executed
whenever the view is rendered or shown and the following conditions are true:

1. It has been shown at least once before
2. It has been rendered at least once before
3. It is a child of the `document`.

##### `bindEntityEvents( target, entity, bindings )`

Bind the `bindings` event hash for `entity` to callbacks on the `target` object. This powers
the `modelEvents` and `collectionEvents` hash of Marionette Views.

##### `unbindEntityEvents( target, entity, bindings )`

Remove the `bindings` for `entity` from `target`.

##### `proxyBindEntityEvents( entity, bindings )`

Executes `bindEntityEvents` with `this` as the target. This is used to give many Marionette Classes `bindEntityEvents` on their prototype.

##### `proxyUbindEntityEvents( entity, bindings )`

Executes `bindEntityEvents` with `this` as the target. This is used to give many Marionette Classes `bindEntityEvents` on their prototype.

##### `triggerMethod( eventName [, args...] )`

This is the primary method for communicating events in Marionette. It allows you to respond to
events both internally to your instance and externally by executing a single method.

First, it converts the `eventName` into a callback name. It does this by converting the colon-separated
`eventName` into camel-case. It then prepends `on` to the resulting word to generate the callback name. For
instance, `some:event` would have the associated `onSomeEvent`.

Once the callback name is generated, it checks to see if it exists on the object. If it exists, it will be
called, passing all of the `args` as the argument. The return value of this method is stored, and is what is ultimately returned by `triggerMethod`.

Next, `trigger` will be called with the same arguments as `triggerMethod`.

Lastly, the value returned by the `onEventName` method is returned.
