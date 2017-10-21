# Rotating the Camera

You can rotate the camera about the _eye_ position, to look around in first-person fashion, or about the _look_ position, to orbit the point you're looking at.

The camera is rotated about each axis individually.

Vertical rotation is gimbal-locked to the World-space Y-axis by default. You can disable that to make the camera pivot about its _up_ vector, for a free trackball type rotation.

### Examples

Disabling gimbal locking:

```javascript
viewer.lockGimbalY(false);
```

Rotating the camera's `eye` about `look`, pivoting around `up`:

```javascript
viewer.rotateEyeY(10);
```

Rotate the camera's `eye` about `look`, pivoting around the axis orthogonal to `eye->look` and `up`:

```javascript
viewer.rotateEyeX(10);
```

Rotate the camera's `look` about `eye`, pivoting around the World-space Y-axis if  
gimbal locking is enabled, otherwise pivoting around `up`:

```javascript
viewer.rotateLookY(10);
```

Rotate the camera's `look` about `eye`, pivoting around the World-space Y-axis if  
gimbal locking is enabled, otherwise pivoting around the axis orthogonal to `eye->look` and `up`:

```javascript
viewer.rotateLookX(10);
```



