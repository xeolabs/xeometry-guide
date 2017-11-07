# Camera Projections

You can switch the camera between perspective and orthographic projections at any time.

### Examples

Switching the camera to orthographic projection:

```javascript
viewer.setProjection("ortho");
```

Setting the camera's orthographic projection properties:

```javascript
viewer.setOrthoScale(2.0); // How many units to fit within view volume
viewer.setOrthoNear(0.1);
viewer.setOrthoFar(8000);
```

Switching the camera to perspective projection:

```javascript
viewer.setProjection("perspective");
```

Setting perspective projection properties:

```javascript
viewer.setPerspectiveFOV(50); // Field of view in degrees
viewer.setPerspectiveNear(0.1);
viewer.setPerspectiveFar(10000);
```

Note that you can get and set properties for each projection at any time, regardless of which one is active.


