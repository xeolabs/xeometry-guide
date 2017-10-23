# Panning the Camera

You can pan the camera along its local axis.

The camera's horizontal panning is along its local horizontal axis, which runs perpendicular to its _eye_->_look_ and _up_ vectors, its vertical panning is along its _up_ axis, and its forward and back panning is along its _eye_->_look_ axis.

Panning translates _eye_ and _look_ in unison, and does not affect _up_.

Panning offsets are incremental, ie. relative to the camera's current position. As you rotate, translate and pan the camera, the only state that it retains is its current _eye_, _look_ and _up_ properties. 

### Examples

Setting an initial camera position:

```
viewer.setEye([0, 0, -100]);
viewer.setLook([0,  0, 0]);
viewer.setUp([0, 1, 0]);

// eye is now [0, 0, -100]
// look is now [0, 0, 0]
// up remains [0, 1, 0]
```

Panning the camera five units to the left:

```javascript
viewer.panCamera([-5, 0, 0]);

// eye is now [-5, 0, -100]
// look is now [-5, 0, 0]
// up remains [0, 1, 0]
```

Panning the camera three units upwards:

```javascript
viewer.panCamera([0, 3, 0]);

// eye is now [-5, 3, -100]
// look is now [-5, 3, 0]
// up remains [0, 1, 0]
```

Panning the camera ten units backwards:

```javascript
viewer.panCamera([0, 0, -10]);

// eye is now [-5, 3 -110]
// look is now [-5, 3, -10]
// up remains [0, 1, 0]
```



