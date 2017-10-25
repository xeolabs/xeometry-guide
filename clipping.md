# Clipping

When you need to look inside your models, you can slice them open with custom clipping planes. Each plane is defined in World space, as a 3D center position and a direction vector. Everything that falls in front of that position, in the direction of the vector, will not be rendered, unless configured unclippable.

### Example

In the example below, we'll position the camera and create a couple of clipping planes with visible helpers that show their position and direction. Then we'll load a glTF model of a reciprocating saw. Once that's loaded, we'll rotate it 90 degrees, so we can view it from the side. Finally, we'll configure a couple of objects unclippable, just to show how that's done.

```javascript
var viewer = new xeometry.Viewer();

viewer.setEye([-130, -40, 350]);
viewer.setLook([-130, -40, 0]);

viewer.createClip("clip1", {
    pos: [-130, -40, 0],
    dir: [0, 0, -1],
    shown: true
});

viewer.createClip("clip2", {
    pos: [-130, 10, 0],
    dir: [0, -1, -1],
    shown: true
});

viewer.loadModel("saw", "ReciprocatingSaw.gltf", function () {
    viewer.setRotate("saw", [90, 0, 0]);
    viewer.setUnclippable(["saw#3.4", "saw#3.2", "saw#3.4"]);
});
```

[![](/assets/Screenshot from 2017-10-25 23-25-13.png)](http://xeolabs.com/xeometry/examples/#guidebook_clipping)

