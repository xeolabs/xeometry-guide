# Rotating the Camera

As described in [_Controlling the camera_](controllingTheCamera.md), a camera's position is given as _eye_ and _look_ positions and an _up_ vector. To perform a first-person rotation, you can rotate the camera's _look_ position and _up_ vector around _eye_. To orbit something, you can rotate the _eye_ position and _up_ vector around _look_.

The camera's pitch rotation is about its local horizontal axis, which runs perpendicular to its _eye_->_look_ and _up_ vectors, and its roll rotation is about its _eye_->_look_ axis.

By default, the camera is gimbal-locked, which makes its yaw rotation pivot around the World-space Y-axis. This is helpful to avoid disorientation. When gimbal lock is disabled, the camera pivots about its local vertical axis, which runs along the camera's _up_ vector.

Rotation degrees are incremental, ie. relative to the camera's current position. As you rotate, translate and pan the camera, the only state that it retains is its current _eye_, _look_ and _up_ properties. 

### Examples

Disabling gimbal locking:

```javascript
viewer.lockGimbalY(false);
```

Rotating the camera's _eye_ about _look_, pivoting around _up_:

```javascript
viewer.rotateEyeY(10);
```

Rotate the camera's _eye_ about _look_, pivoting around the axis orthogonal to _eye_->_look_ and _up_:

```javascript
viewer.rotateEyeX(10);
```

Rotating the camera's _look_ about _eye_, pivoting around the World-space Y-axis if gimbal locking is enabled, otherwise pivoting around _up_:

```javascript
viewer.rotateLookY(10);
```

Rotating the camera's _look_ about _eye_, pivoting around the World-space Y-axis if gimbal locking is enabled, otherwise pivoting around the axis orthogonal to _eye_->_look_ and _up_:

```javascript
viewer.rotateLookX(10);
```


