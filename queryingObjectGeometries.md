# Querying geometry

You can query the geometry of each of the objects in your viewer. This is useful when you want to implement application logic for things like collision detection etc.

Geometry consists of:

* a primitive type,
* array of World-space vertex positions (Float32Array),
* array of tangent-space vertex normal vectors (Float32Array), and
* array of indices (Int16Array or Int32Array), which index the vertex arrays to form primitives.

Transforming an object will modify its vertex positions.

Vertex arrays are flat bu

### Examples

Get an object's primitive type:

```javascript
var primitive = viewer.getPrimitive("saw#43");
```

Possible values for the primitive are: *"points", "lines",
"line-loop", "line-strip", "triangles", "triangle-strip"* and *"triangle-fan"*.

Get the World-space vertex positions of an object:

```javascript
var positions = viewer.getPositions("saw#43");
```

Get the tangent-space vertex normals of an object:

```javascript
var normals = viewer.getNormals("saw#43");
```

Get the indices of an object:

```javascript
var indices = viewer.getIndices("saw#43");
```

