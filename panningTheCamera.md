# Panning the Camera

You can pan the camera along its local axis.

Panning translates the camera's `eye` and `look` positions in unison.

* Horizontal panning moves the camera along the axis perpendicular to `eye->look` and `up`.
* Vertical panning moves the camera along `up`.
* Forward and backward panning moves the camera along the `eye->look` vector.

### Examples

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



