# Controlling the Camera

A viewer has a camera that you can move around the scene.

The camera's position is represented by three World-space vectors:

* _eye_ - the position of your eye,
* _look_ - the point you're looking at
* _up_ - the direction of "up"

Set and get those properties to manage the camera position. 

> Note that these properties are the only state that xeometry tracks for the camera position. In other words, as you rotate, pan and zoom the camera, xeometry does not remember your rotation angles or translation offsets.

### Examples

Setting _eye_, _look_ and _up_ separately:

```javascript
viewer.setEye([0,0,-100]);
viewer.setLook([0,0,0]);
viewer.setUp([0,1,0]);
```

Setting _eye_, _look_ and _up_ in one shot:

```javascript
// Eye, look and "up" vector
viewer.setEyeLookUp([0,0,-100],[0,0,0],[0,1,0], function() {
    // Camera arrived
});
```

Getting the camera position:

```javascript
var eye = viewer.getEye();
var look = viewer.getLook();
var up = viewer.getUp();
```



