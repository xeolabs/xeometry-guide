# Querying Boundaries

Each model and object in a viewer has a boundary, which you can query at any time.

A boundary is an axis-aligned bounding box \(_AABB\)_ in World space. It's represented as an array containing the boundary's minimum and maximum extents for each World-space axis:

```
[xmin, ymin, zmin, xmax, ymax, zmax]
```

Each object's boundary dynamically fits to the World-space extents of the object's geometry vertex positions. This means that an object's boundary will automatically remain fitted to the object whenever you update the object's transforms, or update the transforms of the object's model \(see [_Transforming_](transforming.md)\).

Each model's boundary dynamically fits to the collective boundary of the model's objects. This means that the boundary will automatically remain fitted to the objects whenever you transform one of them, or transform the model itself. Note that object transforms are within the coordinate space set up by their model's transforms.



Whenever you transform a model or an object, you'll automatically update the extents of its boundary \(see [_Transforming_](transforming.md)\).

As shown in the examples below, xeometry has a flexible method that allows you to query either the boundaries of individual models and objects, or the collective boundary of an assortment of models, objects and types.

### Examples

Get the collective boundary of everything in a viewer:

```javascript
var totalBoundary = viewer.getAABB();
// Result: [xmin, ymin, zmin, xmax, ymax, zmax] 
```

Get the boundary of a model:

```javascript
var sawBoundary = viewer.getAABB("saw");
```

Get collective boundary of two objects:

```javascript
var objectsBoundary = viewer.getAABB(["saw34", "saw5"]);
```

Get collective boundary of all objects of the given types \(see [_Assigning types to objects_](assigningTypesToObjects.md)\):

```javascript
var objectsBoundary = viewer.getAABB(["IfcFlowController", "IfcFlowFitting"]);
```

Get collective boundary of two models:

```javascript
var modelsBoundary = viewer.getAABB(["saw", "gearbox"]);
```

Get collective boundary of the first five objects within a given model:

```javascript
var objectsBoundary2 = viewer.getAABB(viewer.objects("saw").slice(0, 5));
```

Get collective boundary of a model plus a couple of objects from a different model:

```javascript
var objectsBoundary3 = viewer.getAABB(["gearbox", "saw#2", "saw#5"]);
```



