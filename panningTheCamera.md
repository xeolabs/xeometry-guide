# Panning the camera

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