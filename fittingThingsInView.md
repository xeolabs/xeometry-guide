# Fitting Things in View

You can fly or jump a xeometry viewer's camera to fit specified models, objects, types or boundaries in view.

### Examples

Configuring the camera to fly for two seconds as it moves to each new target:

```javascript
viewer.setViewFitDuration(2); // Seconds
```

When the duration greater than zero, the camera will fly, otherwise it will jump straight to each new target.

Flying camera to a given position:

```javascript
// Eye, look and "up" vector
viewer.setEyeLookUp([0,0,-100],[0,0,0],[0,1,0], function() {
    // Camera arrived
});
```

Flying the camera to fit everything in view:

```javascript
viewer.viewFit(function() {
    // Camera arrived
});
```

Fly the camera to fit a boundary in view \(see [_Querying Boundaries_](https://www.gitbook.com/book/xeolabs/xeometry/edit#)\):

```javascript
viewer.viewFit([-50,-25,-50, 50, 25, 50], function() {
    // Camera arrived
});
```

> A boundary is an axis-aligned bounding box \(_AABB_\) in World-space, given as an array of  
> values `[xmin, ymin, zmin, xmax, ymax, zmax]`.

Flying the camera to fit a model in view:

```javascript
viewer.viewFit("saw", function() {
    // Camera arrived
});
```

Flying the camera to fit two models in view:

```javascript
viewer.viewFit(["saw", "gearbox"], function() {
    // Camera arrived
});
```

Flying the camera to fit all objects of the given types \(see [_Assigning types to objects_](assigningTypesToObjects.md)\):

```javascript
viewer.viewFit(["IfcFlowController", "IfcFlowFitting"], function() {
    // Camera arrived
});
```

Flying the camera to fit a model, two objects, and all objects of the given type:

```javascript
viewer.viewFit(["gearbox", "saw#1", "saw#5", "IfcFlowFitting"], function() {
    // Camera arrived
});
```

Flying the camera to fit all objects of the given types, looking along the World-space -X axis:

```javascript
viewer.viewFitLeft(["IfcFlowController", "IfcFlowFitting"], function() {
    // Camera arrived
});
```

Flying the camera to fit a model, two objects, and all objects of the given type, looking along the World-space -Y axis:

```javascript
viewer.viewFitTop(["gearbox", "saw#1", "saw#5", "IfcFlowFitting"], function() {
    // Camera arrived
});
```

Configuring the camera to jump directly to each new position:

```javascript
viewer.setViewFitDuration(0);
```

Jumping the camera to a given position:

```javascript
viewer.setEyeLookUp([-100,0,0],[0,0,0],[0,1,0]);
```

Jumping the camera to fit two objects in view - note we don't need the callback anymore because camera is now jumping:

```javascript
viewer.viewFit(["saw34", "saw5"]);
```

Jumping the camera to fit a model and two objects in view:

```javascript
viewer.viewFit(["gearbox", "saw#2", "saw#5"]);
```

Setting how much of the field of view that a target boundary will occupy when flying the camera to fit models or objects to the view:

```javascript
viewer.setViewFitFOV(20); // Degrees
var fitFOV = viewer.fitFOV();
```



