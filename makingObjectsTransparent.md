# Transparent objects

You can make objects transparent, to reveal other objects behind or inside them.

[![](assets/outlining.png)](http://xeolabs.com/xeometry/examples/#effects_outlining)

````javascript
var viewer = new xeometry.Viewer();

viewer.loadModel("gearbox", "GearboxAssy.gltf", function () {

    viewer.viewFit();

    viewer.setOpacity(0.5);

    viewer.setOpacity([
        "gearbox#1", "gearbox#1.0", "gearbox#1.1", "gearbox#1.2" // ...
    ], 1.0);
});
````