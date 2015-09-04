# Lifecycle

## created

Called once the element is created.

```
Polymer({
  is: 'foo-element',
  created: function () {
    console.log('Created!', this);
  }
});
```

## attached

Called every time the element is (re)attached to the DOM tree.

```
Polymer({
  is: 'foo-element',
  attached: function () {
  	console.log('Attached!', this);
  }
});
```

## detached

Called every time the element is detached from the DOM tree.

```
Polymer({
  is: 'foo-element',
  detached: function () {
  	console.log('Detached!', this);
  }
});
```

## attributeChanged

Called every time an attribute is added, removed, or changed. The callback is called with three arguments - attribute name, old attribute value, and new attribute value.

```
Polymer({
  is: 'foo-element',
  attributeChanged: function (name, oldValue, newValue) {
  	console.log(name, oldValue, newValue);
  }
});
```

## ready

Called once the element's local DOM is ready.

```
Polymer({
  is: 'foo-element',
  ready: function () {
  	console.log('Ready!');
  }
});
```

