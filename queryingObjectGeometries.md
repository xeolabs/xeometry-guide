# Querying object geometries

You can query the geometry of each of the objects in your viewer. This is useful when you want to implement application logic for things like collision detection etc.

Geometry consists of World-space vertex positions, a primitive type, and indices, which link the positions together according to the primitive type.

Transforming an object will update its vertex positions.

### Examples

Get the World-space vertex positions of an object:

```javascript
var positions = viewer.getPositions("saw#43");
```

Get the indices of an object:

```javascript
var indices = viewer.getIndices("saw#43");
```

Get an object's primitive type:

```javascript
var primitive = viewer.getPrimitive("saw#43");
```

Possible values for the primitive are 'points', 'lines',  
'line-loop', 'line-strip', 'triangles', 'triangle-strip' and 'triangle-fan'.

