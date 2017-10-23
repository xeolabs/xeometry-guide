# Rotating the Camera

To perform a first-person rotation, xeometry rotates the camera's _look_ and _up_ around _eye_.  To orbit the point you're look at, it rotates _eye_ and _up_ around _look_.

The camera's pitch rotation is around its local horizontal axis, which is perpendicular to its _eye_->_look_ and _up_ vectors. Its roll rotation is around its _eye_->_look_ vector.

The camera is gimbal-locked by default. This means that its yaw rotation spins around the World-space Y-axis. This is helpful to avoid disorientation and makes the rotation easier to control with the mouse. When you disable gimbal lock, the camera's yaw rotation spins around its _up_ vector, which allows it to rotate freely, like a trackball.

Rotation degrees are incremental, ie. relative to the camera's current position. 

> Note that as you rotate, translate and pan the camera, the only state that xeometry remembers is the camera's current _eye_, _look_ and _up_ values (ie. it doesn't remember any rotation angles).  

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


