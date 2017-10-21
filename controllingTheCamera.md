# Controlling the Camera

A viewer has a single camera that you can move around the scene.

The camera's position is represented by three World-space vectors:

* _eye_ - the position of your eye,
* _look_ - the position of the point you're looking at
* _up_ - the direction of "up"

You can set and get those directly, to manage the camera position.

### Examples

Setting the camera position:

```javascript
viewer.setEye([0,0,-100]);
viewer.setLook([0,0,0]);
viewer.setUp([0,1,0]);
```

Getting the camera position:

```javascript
var eye = viewer.getEye();
var look = viewer.getLook();
var up = viewer.getUp(); 
```



