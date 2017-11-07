# Querying Geometry

Each object in your xeometry viewer has a geometry, which describes its shape.

A geometry consists of:

* a primitive type \(_"points", "lines", "line-loop", "line-strip", "triangles", "triangle-strip"_ or _"triangle-fan"\),_
* an array of World-space vertex positions \(_Float32Array_\),
* an array of tangent-space vertex normal vectors \(_Float32Array_\), and
* an array of indices \(_Int16Array_ or _Int32Array_\), which index the vertex arrays to form primitives[^1].

### Examples

Getting an object's geometry primitive type:

```javascript
var primitive = viewer.getPrimitive("saw#43");
// Eg. "triangles"
```

Getting the World-space vertex positions of the geometry of the object:

```javascript
var positions = viewer.getPositions("saw#43");
// Eg. [2,2,2,-2,2,2,-2,-2,2,2,-2,2,2,2,2,2,-2,2,2,-2,-2,2,2,-2,

            // v0-v1-v6-v1 top
            2, 2, 2,
            2, 2, -2,
            -2, 2, -2,
            -2, 2, 2,

            // v1-v6-v7-v2 left
            -2, 2, 2,
            -2, 2, -2,
            -2, -2, -2,
            -2, -2, 2,

            // v7-v4-v3-v2 bottom
            -2, -2, -2,
            2, -2, -2,
            2, -2, 2,
            -2, -2, 2,

            // v4-v7-v6-v1 back
            2, -2, -2,
            -2, -2, -2,
            -2, 2, -2,
            2, 2, -2]
```

Note that the value of these positions will change whenever we transform the object \(see [_Transforming_](transforming.md)\).

Getting the tangent-space vertex normal vectors of the geometry of the object:

```javascript
var normals = viewer.getNormals("saw#43");
```

Get the indices of the geometry of the object:

```javascript
var indices = viewer.getIndices("saw#43");
```

Get the World-space boundary of an object's geometry's vertex positions \(see [_Querying Boundaries_](queryingBoundaries.md)\):

```javascript
var aabb = viewer.getAABB("saw#43");
```

Note that the extents of this boundary will change whenever we transform the object \(see [_Transforming_](transforming.md)\).

[^1]: The primitive type indicates the layout of the indices array - see [The OpenGL Wiki](https://www.khronos.org/opengl/wiki/Primitive) for more information.

