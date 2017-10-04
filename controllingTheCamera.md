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
