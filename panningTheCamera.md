# Panning the Camera

A xeometry viewer's camera can be panned on three axis:

* horizontally, along its local horizontal axis, which runs perpendicular to its _eye_-&gt;_look_ and _up_ vectors, 
* vertically, along its _up_ axis, and 
* forwards and backwards, along its _eye_-&gt;_look_ axis.

Panning translates _eye_ and _look_ in unison, and does not affect _up_.

Panning offsets are incremental, ie. relative to the camera's current position.

### Examples

Setting an initial camera position:

```javascript
viewer.setEye([0, 0, -100]);
viewer.setLook([0,  0, 0]);
viewer.setUp([0, 1, 0]);
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



