# Intro

## Setup 

Create a `bower.json` file.

```
> bower init
```

Tell bower where you want your components installed by creating a file named `.bowerrc` with a content like this.

```json
{
  "directory": "public/components"
}
```

Add Polymer as a dependency.

```
> bower install --save Polymer/polymer
```

## Creating an Element

Create a file named `foo-element.html` in the `public` folder, and give it the following content.

```html
<link rel="import" href="components/polymer/polymer.html">
<dom-module id="foo-element">
  <style>
  </style>
  <template>
  </template>
  <script>
    Polymer({
      is: 'foo-element'
    });
  </script>
</dom-module>
```

### Creating a constructor

The `Polymer` function will return a constructor for the newly registered element. Script tags inside the `dom-module` tag will be executed in global scoop (like all other script tags) - so we can save a reference to the constructor like this.

```html
<script>
  var FooElement = Polymer({
    is: 'foo-element'
  });
</script>
```

### Passing arguments to the constructor

Sometimes it is convenient to pass arguments to an elements constructor. This can be done by implementing the `factoryImpl` method.

```javascript
var FooElement = Polymer({
  is: 'foo-element',
  factoryImpl: function(bar) {
  	this.bar = bar;
  }
});
```

## Using an Element

Create a `index.html` file in the `public` folder, and give it the following content.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Intro</title>
  <script src="components/webcomponentsjs/webcomponents-lite.min.js"></script>
  <link rel="import" href="foo-element.html">
</head>
<body>
  <foo-element></foo-element>
</body>
<script>
  window.addEventListener('WebComponentsReady', function() {
    var foo = document.querySelector('foo-element');
  });
</script>
</html>

```

## Extending Native Elements

A native element is extended by setting the `extends` property on the prototype.

```javascript
Polymer({
  is: 'foo-input',
  extends: 'input'
  }
});
```

To use the extended version of the element set the `is` attribute on the element.

```html
<input is="foo-input">
```
or create the element in JavaScript via the DOM API.

```javascript
var foo = window.document.createElement('input', 'foo-input');
```
