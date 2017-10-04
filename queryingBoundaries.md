# Querying boundaries

You can dynamically query the boundaries of models and objects in your viewer.

A boundary is an axis-aligned bounding box \(_AABB_\) in World-space, given as an array of values `[xmin, ymin, zmin, xmax, ymax, zmax]`.

Transforming a model or object will update its boundary.

---

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

Get collective boundary of all objects of the given types:

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



