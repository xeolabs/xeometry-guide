# Clipping

You can create an unlimited number of arbitrarily-positioned clipping planes in your viewer. You can also mask which
objects are clipped by them.

### Example

In the example below, we'll position the camera and create a clipping plane that passes through the World-space origin
and discards everything on the +Z side. Then we'll load a glTF model of a reciprocating saw, which will get sliced in
half by our clipping  plane, to reveal some of its inner workings.

````javascript
var viewer = new xeometry.Viewer();

viewer.setEye([-130, -40, 350]);
viewer.setLook([-130, -40, 0]);

viewer.createClip("clip1", {pos: [0, 0, 0], dir: [0, 0, -1]});

viewer.loadModel("saw", "ReciprocatingSaw.gltf", function () {
    viewer.setRotate("saw", [90, 0, 0]);
});
````
[![](assets/clipping.png)](http://xeolabs.com/xeometry/examples/#guidebook_clipping)

