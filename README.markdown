Available on [GitHub](https://github.com/dcporter/mvcobject).

## Super Lightweight JS Binding & KVO

When even Angular is overkill, drop in MVCObject.js for fast, easy, lightweight binding
and KVO.

This object implements the Google Maps API's very useful MVCObject interface, documented
[here](https://developers.google.com/maps/documentation/javascript/reference#MVCObject).
This project is forked from [this](https://code.google.com/p/mvcobject-js/) excellent but
apparently abandoned one; John and Mark deserve the credit. This version tones down the
object's tendency to throw errors, making it much friendlier to use.

### Example

Binding:

```javascript

var objectA = new MVCObject(),
	objectB = new MVCObject();

// Always use setters and getters.
objectA.set('name', 'John');
objectB.set('name', 'Mark');

// Set up a binding - one line. This syncs the values, overrides the value on objectB.
objectB.bindTo('name', objectA);

objectB.get('name');
// > 'John'

objectA.set('name', 'Dave');
objectB.get('name');
// > 'Dave'
```

Key-Value Observing:
```JavaScript
var objectA = new MVCObject();
objectA.set('name', 'John');

objectA.name_changed = function() { console.log("Name changed to: " + this.get('name')); };

objectA.set('name', 'Dave');
// > "Name changed to: Dave"
```

Subclassing (obvious but very handy):

```javascript
ObjectA = function() {};
ObjectA.prototype = new MVCObject();
ObjectA.prototype.constructor = ObjectA;
```

### License

Like its predecessor, this is available under the Apache License 2.0 (see included LICENSE).
