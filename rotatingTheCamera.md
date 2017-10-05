# Rotating the camera

You can rotate the camera incrementally, either rotating `eye` about `look` \(orbiting\), or rotating `look` about `eye` \(first-person rotation\).

Vertical rotation is gimbal-locked to the World-space Y-axis by default. You can disable that to make the camera pivot about its `up` vector, for more of a trackball type rotation.

### Examples

Disable gimbal locking:

```javascript
viewer.lockGimbalY(false);
```

Rotate the camera's `eye` about `look`, pivoting around `up`:

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



