### Template Cache

The TemplateCache is a Class that manages your View's templates. Although we highly
recommend that you precompile your templates, the TemplateCache is a way for you
to serve up uncompiled templates in your applications in an efficient way. It works
with `templateId`s, which are query strings that point to the script tag containing
your template.

#### Prototype Methods

##### constructor( templateId )

Stores the `templateId` on the instance.

##### load

Returns the compiled template. If the template has not been rendered it will be
done so; otherwise it returns the cached compiled template.

##### loadTemplate( templateId )

Obtains and returns the HTML from the `templateId` element, where `templateId`
is a query selector string. If the element does not exist, or is a falsey value,
then an Error is thrown.

##### compileTemplate( rawTemplate )

The method that actually does the work of compiling a template. Override this
if you're using a templating language other than Underscore. The default method is
simply:

```js
return _.template(rawTemplate);
```

#### Class Methods

##### `get( templateId )`

Get a template by Id. If the template has not been compiled, it will compile it
and then cache it. If it has been compiled before then it will return the
compiled version instead.

##### `clear( [templateId1, templateId2...] )`

Clear any number of templates from the cache. Each Id passed in will
be cleared. Pass no arguments to clear the entire cache.

#### Prototype Properties

##### templateId

The query selector that points to the script tag containing your template. For
instance, `#my-template`.

##### compiledTemplate

Once the TemplateCache's template has been compiled once it is available as
the `compiledTemplate` property.

#### Class Properties

These are properties that are stored directly on the `Marionette.TemplateCache`
object. They are unavailable to instances of the TemplateCache.

##### templateCaches

The internal store for templates.

