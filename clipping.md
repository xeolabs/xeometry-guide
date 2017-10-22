# Clipping

You can create custom clipping planes in your viewer, to slice open your models so that you can see inside them. 

Clipping planes You can also mask which objects are clipped by them.

### Example

In the example below, we'll position the camera and create a clipping plane that passes through the World-space origin  
and discards everything on the +Z side. Then we'll load a glTF model of a reciprocating saw. Once that's loaded, we'll rotate it 90 degrees, so we can view it from the side, and set two objects unclippable.  which will get sliced in half by our clipping  plane, to reveal some of its inner workings.  TODO TODO  TODO

```javascript
var viewer = new xeometry.Viewer();

viewer.setEye([-130, -40, 350]);
viewer.setLook([-130, -40, 0]);

viewer.createClip("clip1", {pos: [0, 0, 0], dir: [0, 0, -1]});

viewer.loadModel("saw", "ReciprocatingSaw.gltf", function () {
    viewer.setRotate("saw", [90, 0, 0]);
    viewer.setUnclippable(["saw#3.4", "saw#3.2", "saw#3.4"]);
});
```

[![](assets/clipping.png)](http://xeolabs.com/xeometry/examples/#guidebook_clipping)

