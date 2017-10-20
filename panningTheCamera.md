# Panning the Camera

You can pan the camera along its local axis.

* Horizontal panning moves the camera along the axis perpendicular to its _eye_-&gt;_look_ and _up_ vectors.
* Vertical panning moves the camera along its _up _vector_._
* Forward and backward panning moves the camera along its _eye_-&gt;_look_ vector.

Panning translates _eye_ and _look_ in unison, and does not affect _up_.

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



