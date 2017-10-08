# Transparent objects

You can make objects transparent, to reveal other objects behind or inside them.

[![](assets/transparency
.png)](http://xeolabs.com/xeometry/examples/#guidebook_transparency)

````javascript
var viewer = new xeometry.Viewer();

viewer.setEye([-145.22, -32.97, 282.5]);
viewer.setLook([-147.68, -20.64, 0]);
viewer.setUp([0, 1, 0]);

viewer.loadModel("saw", "ReciprocatingSaw.gltf", function () {
    viewer.setRotate("saw", [90, 0, 0]);
    viewer.setOpacity([
        "saw#1", "saw#1.28", "saw#1.1",
        "saw#1.0", "saw#1.2", "saw#1.3",
        "saw#1.4", "saw#1.5", "saw#1.7"
        ], 0.3);
});
````