# Querying geometry

You can query the geometry of each of the objects in your viewer. This is useful when you want to implement application
logic for things like collision detection etc.

Geometry consists of:

* a primitive type,
* array of World-space vertex positions (Float32Array),
* array of tangent-space vertex normal vectors (Float32Array), and
* array of indices (Int16Array or Int32Array), which index the vertex arrays to form primitives.

Note that transforming an object will modify its vertex positions (see *[Transforming](transforming.md)*).

### Examples

Get an object's primitive type:

```javascript
var primitive = viewer.getPrimitive("saw#43");
```

Possible values for the primitive are: *"points", "lines",
"line-loop", "line-strip", "triangles", "triangle-strip"* and *"triangle-fan"*.

Get an object's World-space vertex positions:

```javascript
var positions = viewer.getPositions("saw#43");
```

Get an object's tangent-space vertex normals:

```javascript
var normals = viewer.getNormals("saw#43");
```

Get the indices of an object:

```javascript
var indices = viewer.getIndices("saw#43");
```

Get the World-space boundary of an object's vertex positions (see *[Querying Boundaries](queryingBoundaries.md)*):

```javascript
var aabb = viewer.getAABB("saw#43");
```
