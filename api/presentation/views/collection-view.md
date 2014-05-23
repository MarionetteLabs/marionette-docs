### Collection View  
Extends from `Marionette.View`

The CollectionView does exactly what it's name suggests: it renders a collection. It can be used when you wish
to take a Collection and produce a group of child Views to represent each model in the Collection. This is useful
when you want to, for instance, listen to model events on a per-view basis.

For simple lists, where you only need HTML output, it is suggested that you use an ItemView. And if you need to wrap your
rendered Collection in a template then the CompositeView is recommended.
