# Controlling the Camera

A viewer has a single camera that you can move around the scene.

A camera position is represented by three World-space vectors:

* _eye_ - the position of your eye,
* _look_ - the position of the point you're looking at
* _up_ - the direction of "up"

You can set and get those directly, to manage the camera position:

```
// Set position of the camera
viewer.setEye([0,0,-100]);
viewer.setLook([0,0,0]);
viewer.setUp([0,1,0]);

// Get the camera position
var eye = viewer.getEye();
var look = viewer.getLook(); 
var up = viewer.getUp();
```

The xeometry viewer also provides various convenience methods to move the camera

The camera projection can be either

* perspective - 
* orthographic

### Examples

Getting the camera eye position, point-of-interest and "up" vector:

```javascript
var eye = viewer.getEye();// Position of eye
// Eg. [0.0, 0.0, -10.0]

var look = viewer.getLook(); // point we're looking at
// Eg. [0.0, 0.0, 0.0]

var up = viewer.getUp(); // Direction of "up"
// Eg. [0.0, 0.0, 1.0]
```

Setting camera `eye`, `look` and `up`:

```javascript
viewer.setEye([0,0,-100]);
viewer.setLook([0,0,0]);
viewer.setUp([0,1,0]);
```



