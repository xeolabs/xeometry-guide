# Querying viewer content

## Getting models and objects

You can query the models and objects that are currently loaded in your viewer.

The ID of each object is prefixed by the ID of its model, ie. "&lt;model ID&gt;#&lt;object ID&gt;". Each object
corresponds to a ````node```` element within its model's glTF file. If the ````node```` has a ````name```` attribute,
then that's used for the object part of the ID, eg. "saw#outerCasing". Otherwise, the index of the ````node```` within
the flTF file's ````nodes```` section is used, eg. "saw#23".

Get all models:
````javascript
var models = viewer.getModels();
````

Get all objects:
````javascript
var objects = viewer.getObjects();
````

Get all objects in a model:
````javascript
var saw = viewer.getObjects("saw");
````

Get an object's model:
````javascript
var model = viewer.getModel("saw#23");
````

## Getting boundaries

You can dynamically query the boundaries of models and objects in your viewer.

A boundary is an axis-aligned bounding box (*AABB*) in World-space, given as an array of values ````[xmin, ymin, zmin, xmax, ymax, zmax]````.

Transforming a model or object will update its boundary.

Get the collective boundary of everything in a viewer:
````javascript
var totalBoundary = viewer.getAABB();
````

Get the boundary of a model:
````javascript
var sawBoundary = viewer.getAABB("saw");
````

Get collective boundary of two objects:
````javascript
var objectsBoundary = viewer.getAABB(["saw34", "saw5"]);
````

Get collective boundary of all objects of the given types:
````javascript
var objectsBoundary = viewer.getAABB(["IfcFlowController", "IfcFlowFitting"]);
````

Get collective boundary of two models:
````javascript
var modelsBoundary = viewer.getAABB(["saw", "gearbox"]);
````

Get collective boundary of the first five objects within a given model:
````javascript
var objectsBoundary2 = viewer.getAABB(viewer.objects("saw").slice(0, 5));
````

Get collective boundary of a model plus a couple of objects from a different model:
````javascript
var objectsBoundary3 = viewer.getAABB(["gearbox", "saw#2", "saw#5"]);
````

## Getting object geometries

You can query the geometry of each of the objects in your viewer. This is useful when
you want to implement application logic for things like collision detection etc.

Geometry consists of World-space vertex positions, a primitive type, and indices, which link
the positions together according to the primitive type.

Transforming an object will update its vertex positions.

Get the World-space vertex positions of an object:
````javascript
var positions = viewer.getPositions("saw#43");
````

Get the indices of an object:
````javascript
var indices = viewer.getIndices("saw#43");
````

Get an object's primitive type:
````javascript
var primitive = viewer.getPrimitive("saw#43");
````

Possible values for the primitive are 'points', 'lines',
'line-loop', 'line-strip', 'triangles', 'triangle-strip' and 'triangle-fan'.

