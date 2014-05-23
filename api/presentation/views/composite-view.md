### Composite View  
Extends from `Marionette.CollectionView`

The CompositeView is like a CollectionView with a template. It allows you to render a list
within a wrapped template, unlike the CollectionView which has no template. The most common
use case for a CompositeView is rendering a table.

Another, less-frequently-used feature of CompositeView is its recursive behavior. If a
ChildView is not specified for the CompositeView, then the CompositeView Class itself will
be used as the ChildView. This allows you to create deeply nested DOM structures. Perhaps the
most common example of this are comment threads in blogs, where comments can have comments,
which themselves can have comments.
