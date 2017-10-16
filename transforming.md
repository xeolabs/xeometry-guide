## Transforming

You can independently transform each model and object in your viewer.

````javascript
var viewer = new xeometry.Viewer();

viewer.setEye([53.06, -198.07, 302.47]);
viewer.setLook([-110.88, -24.57, 87.87]);
viewer.setUp([0.38, 0.76, 0.50]);

viewer.loadModel("saw", "models/gltf/ReciprocatingSaw/glTF-MaterialsCommon/ReciprocatingSaw.gltf", function () {
    viewer.setRotate("saw", [90, 0, 0]);
    viewer.setTranslate("saw#3.1", [0, 80, -50]);
    viewer.setRotate("saw#3.1", [-90, 0, 0]);
});

````
[![](assets/transforms.png)](http://xeolabs.com/xeometry/examples/#guidebook_transforming)

A transform consists of the following operations, applied in this order:

1. scale
2. X-axis rotation \(degrees\),
3. Y-axis rotation,
4. Z-axis rotation
5. translation

An object's transform is relative to its model's transform.

Transforming an object will dynamically update its boundary and geometry vertex positions.

Transforming a model will dynamically update its boundary, along with the boundary and geometry vertex positions of each
of its objects.

### Examples

Translate a model along the X axis, scale it, then rotate it 90 degrees about its X-axis:

```javascript
viewer.setTranslate("saw", [100,0,0]);
viewer.setScale("saw", [0.5,0.5,0.5]);
viewer.setRotate("saw", [90,0,0]);
`
```

Spin an object about its Y-axis:

```javascript
var angles =[0,0,0]; // Tait-Bryant angles about X, Y and Z, in degrees
function spin() {
    viewer.setRotate("saw#2", angles);
    angles[1] += 0.1;
    requestAnimationFrame(spin);
}
spin();
`
```

Get an object's translation, scale and rotation:

```javascript
var translate = viewer.setTranslate("saw");
var scale = viewer.setScale("saw");
var rotate = viewer.setRotate("saw");
`
```


