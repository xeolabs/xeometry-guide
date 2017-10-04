# Controlling the camera

A viewer has a single camera that can be moved in orbit or first-person mode, directed to fit target
elements in view, and switched between perspective and orthographic projections.

Getting camera ````eye````, ````look```` and ````up````:
````javascript
var eye = viewer.getEye();
var look = viewer.getLook();
var up = viewer.getUp();
````

Setting camera ````eye````, ````look```` and ````up````:
````javascript
viewer.setEye([0,0,-100]);
viewer.setLook([0,0,0]);
viewer.setUp([0,1,0]);
````

## Fitting things in view

You can fly or jump the camera to fit given models, objects, types or boundaries in view.

Configure camera to fly for two seconds as it moves to each new target:
````javascript
viewer.setViewFitDuration(2); // Seconds
````

When the duration greater than zero, the camera will fly, otherwise it will jump straight to each new target.

Fly camera to given position:
````javascript
// Eye, look and "up" vector
viewer.setEyeLookUp([0,0,-100],[0,0,0],[0,1,0], function() {
    // Camera arrived
});
````

Fly camera to fit everything in view:
````javascript
viewer.viewFit(function() {
    // Camera arrived
});
````

Fly camera to fit a boundary in view:
````javascript
viewer.viewFit([-50,-25,-50, 50, 25, 50], function() {
    // Camera arrived
});
````
> A boundary is an axis-aligned bounding box (*AABB*) in World-space, given as an array of
values ````[xmin, ymin, zmin, xmax, ymax, zmax]````.

Fly camera to fit a model in view:
````javascript
viewer.viewFit("saw", function() {
    // Camera arrived
});
````

Fly camera to fit two models in view:
````javascript
viewer.viewFit(["saw", "gearbox"], function() {
    // Camera arrived
});
````

Fly camera to fit all objects of the given types:
````javascript
viewer.viewFit(["IfcFlowController", "IfcFlowFitting"], function() {
    // Camera arrived
});
````

Fly camera to fit a model, two objects, and all objects of the given type:
````javascript
viewer.viewFit(["gearbox", "saw#1", "saw#5", "IfcFlowFitting"], function() {
    // Camera arrived
});
````

Fly camera to fit all objects of the given types, looking along the World-space -X axis:
````javascript
viewer.viewFitLeft(["IfcFlowController", "IfcFlowFitting"], function() {
    // Camera arrived
});
````

Fly camera to fit a model, two objects, and all objects of the given type, looking along the World-space -Y axis:
````javascript
viewer.viewFitTop(["gearbox", "saw#1", "saw#5", "IfcFlowFitting"], function() {
    // Camera arrived
});
````

Set camera to jump directly to each new position:
````javascript
viewer.setViewFitDuration(0);
````

Jump camera to given position:
````javascript
viewer.setEyeLookUp([-100,0,0],[0,0,0],[0,1,0]);
````

Jump camera to fit two objects in view - note we don't need the callback anymore because camera is now jumping:
````javascript
viewer.viewFit(["saw34", "saw5"]);
````

Jump camera to fit a model and two objects in view:
````javascript
viewer.viewFit(["gearbox", "saw#2", "saw#5"]);
````

Set how much of the field of view that a target boundary will occupy when flying the camera to fit models or objects to the view:
````javascript
viewer.setViewFitFOV(20); // Degrees
var fitFOV = viewer.fitFOV();
````

## Panning the camera

You can pan the camera incrementally along its local axis.

Panning translates the camera's ````eye```` and ````look```` positions in unison.

* Horizontal panning moves the camera along the axis perpendicular to ````eye->look```` and ````up````.
* Vertical panning moves the camera along ````up````.
* Forward and back panning moves the camera along the ````eye->look```` vector.

Pan camera ````eye```` and ````look```` five units along the axis orthogonal to ````eye->look```` and ````up````:
````javascript
viewer.panCamera([-5, 0, 0]);
````

Pan camera backwards 10 units along the ````eye->look```` vector:
````javascript
viewer.panCamera([0, 0, -10]);
````

## Rotating the camera

You can rotate the camera incrementally, either rotating ````eye```` about ````look```` (orbiting),
or rotating ````look```` about ````eye```` (first-person rotation).

Vertical rotation is gimbal-locked to the World-space Y-axis by default. You can disable that
 to make the camera pivot about its ````up```` vector, for more of a trackball type rotation:
````javascript
viewer.lockGimbalY(false);
````

Rotate the camera's ````eye```` about ````look````, pivoting around ````up````:
````javascript
viewer.rotateEyeY(10);
````

Rotate the camera's ````eye```` about ````look````, pivoting around the axis orthogonal to ````eye->look```` and ````up````:
````javascript
viewer.rotateEyeX(10);
````

Rotate the camera's ````look```` about ````eye````, pivoting around the World-space Y-axis if
gimbal locking is enabled, otherwise pivoting around ````up````:
````javascript
viewer.rotateLookY(10);
````

Rotate the camera's ````look```` about ````eye````, pivoting around the World-space Y-axis if
gimbal locking is enabled, otherwise pivoting around the axis orthogonal to ````eye->look```` and ````up````:
````javascript
viewer.rotateLookX(10);
````

## Zooming the camera

You can zoom the camera incrementally, which changes the distance of ````eye```` from ````look````.

Zoom the ````eye```` towards ````look```` by 12.3 units:
````javascript
viewer.zoom(12.3);
````

Zoom the ````eye```` away from ````look```` by 5 units:
````javascript
viewer.zoom(-5);
````

## Camera projections

You can switch the camera between perspective and orthographic projection at any time.

Switch camera to orthographic projection:
````javascript
viewer.setProjection("ortho");
````
Set orthographic projection properties:
````javascript
viewer.setOrthoScale(2.0); // How many units to fit within view volume
viewer.setOrthoNear(0.1);
viewer.setOrthoFar(8000);
````

Switch camera to perspective projection:

````javascript
viewer.setProjection("perspective");
````

Set perspective projection properties:
````javascript
viewer.setPerspectiveFOV(45); // Field of view in degrees
viewer.setPerspectiveNear(0.1);
viewer.setPerspectiveFar(10000);
````

Note that you can get and set properties for each projection at any time, regardless of which one is active.

## CameraControl

TODO

````javascript
var cameraControl = new xeometry.CameraControl(viewer, {
    firstPerson: false,
    mouseOrbitSens : 1.0,
    mousePanSens : 0.1,
    mouseZoomSens: 1.0
});
````