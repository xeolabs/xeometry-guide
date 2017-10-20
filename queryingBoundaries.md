# Querying Boundaries

Each model and object in a viewer has a boundary, which you can query at any time.

A boundary is an axis-aligned bounding box \(_AABB\)_ in World space. It's represented as an array containing the boundary's minimum and maximum extents on each World-space axis:

```
[xmin, ymin, zmin, xmax, ymax, zmax]
```

Each object's boundary dynamically fits to the World-space extents of the object's geometry vertex positions \(see [_Querying Geometry_](https://www.gitbook.com/book/xeolabs/xeometry/edit#)\). This means that an object's boundary will automatically remain fitted to the object whenever you update the object's transforms, or update the transforms of the object's model \(see [_Transforming_](transforming.md)\).

Each model's boundary dynamically fits to the collective boundary of the model's objects. This means that the boundary will automatically remain fitted to the objects whenever you transform one of them, or transform the model itself. Note that object transforms are within the coordinate space set up by their model's transforms.

As shown in the examples below, a xeometry viewer has a _getAABB\(\)_ method that allows you to query either the boundaries of individual models and objects, or the collective boundary of some random assortment of models, objects and types.

This functionality supports xeometry's ability to auto-fit the camera to specified models or objects \(see [_Fitting things in view_](fittingThingsInView.md)\).

### Examples

Getting the collective boundary of everything in a viewer:

```javascript
var totalBoundary = viewer.getAABB();
```

Getting the boundary of a model:

```javascript
var sawBoundary = viewer.getAABB("saw");
```

Getting the collective boundary of two objects:

```javascript
var objectsBoundary = viewer.getAABB(["saw34", "saw5"]);
```

Getting the collective boundary of all objects of the given types \(see [_Assigning types to objects_](assigningTypesToObjects.md)\):

```javascript
var objectsBoundary = viewer.getAABB(["IfcFlowController", "IfcFlowFitting"]);
```

Getting the collective boundary of two models:

```javascript
var modelsBoundary = viewer.getAABB(["saw", "gearbox"]);
```

Getting the collective boundary of the first five objects within a given model:

```javascript
var objectsBoundary2 = viewer.getAABB(viewer.objects("saw").slice(0, 5));
```

Getting the collective boundary of a model and a couple of objects from a different model:

```javascript
var objectsBoundary3 = viewer.getAABB(["gearbox", "saw#2", "saw#5"]);
```



