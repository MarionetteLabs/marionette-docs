###  Renderer

The Renderer object is a singleton that combines a template method with its data,
rendering it as HTML. Every View in Marionette delegates the task of rendering
templates to this object.

#### Methods

##### `render( template, data )`

This method receives a template as the first argument and the data as the second. It
must return the rendered DOM. The default implementation first checks if the template
is falsey. If it is, then an Error is thrown. If it does exist, it checks to see
if the template is a function. If it isn't, then it uses the TemplateCache object
to get a cached version of the compiled template. Finally, once the template is a
function is calls it, passing in `data` as the first argument, and returns its value.
