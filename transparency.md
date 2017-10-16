# Transparency

You can make objects transparent, to reveal other objects behind or inside them.

### Example

In the example below, we'll load a glTF model of a reciprocating saw, then make its handle transparent, to reveal its inner workings.

```javascript
var viewer = new xeometry.Viewer();

viewer.setEye([-130, -40, 350]);
viewer.setLook([-130, -40, 0]);

viewer.loadModel("saw", "ReciprocatingSaw.gltf", function () {
    viewer.setRotate("saw", [90, 0, 0]);
    viewer.setOpacity(["saw#3.1", "saw#3.2"], 0.5);
});
```

[![](assets/transparency.png)](http://xeolabs.com/xeometry/examples/#guidebook_transparency)

