# Querying Boundaries

Each model and object in a viewer has a boundary. 

Each object's boundary dynamically fits to the World-space extents of the object's geometry vertex positions. This means that an object's boundary will automatically remain fitted to the object whenever you've updated the object's transforms, or updated the transforms of the object's model \(see [_Transforming_](transforming.md)\).

Each model's boundary dynamically fits to the collective boundary of the model's objects. This means that the boundary will automatically remain fitted to the objects whenever you transform one them, or transform the model itself.    

Each object's boundary that encloses provided as an axis-aligned bounding box \(_AABB\)_.

Whenever you transform a model or an object, you'll automatically update the extents of its boundary \(see [_Transforming_](transforming.md)\).

As shown in the examples below, xeometry has a flexible method that allows you to query either the boundaries of individual models and objects, or the collective boundary of an assortment of models, objects and types.

### Examples

Get the collective boundary of everything in a viewer:

```javascript
var totalBoundary = viewer.getAABB();
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



