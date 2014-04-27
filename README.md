bad-element
================

When you're creating a Polymer element _which you intend to share with the world_, you should **never** hard code the path to your `bower_components` directory into your element.

For example:

```
<!-- This is bad. Don't do it >:( -->
<link rel="import" href="bower_components/polymer/polymer.html">

<polymer-element name="bad-element">
  ...
</polymer-element>
```

When a user attempts to install your element, it will be moved inside of _their_ `bower_components` directory, so the structure will look like this:

```
bower_components/
  bad-element/
  polymer/
  platform/
index.html
```

Because `bad-element` is attempting to import `bower_components/polymer/polymer.html` but it reside inside of the user's bower_components directory, it will 404.

## Solution

To fix this issue you should always assume the directory that contains Polymer (or any of your element's other dependencies) is a sibling. This would mean updating your import to look like this:

```
<!-- Yay! :D -->
<link rel="import" href="../polymer/polymer.html">

<polymer-element name="good-element">
  ...
</polymer-element>
```

## [Follow our guide to creating reusable Polymer elements](http://www.polymer-project.org/docs/start/reusableelements.html)
