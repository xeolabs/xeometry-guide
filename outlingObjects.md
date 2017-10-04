# Outlining objects

You can emphasize objects in your viewer by displaying outlines around them.

[![](assets/outlining.png)](http://xeolabs.com/xeometry/examples/#effects_outlining)

````javascript
var viewer = new xeometry.Viewer();

viewer.loadModel("gearbox", "GearboxAssy.gltf", function () {

    viewer.viewFit();

    viewer.setOutlineColor([1, 1, 0]);
    viewer.setOutlineThickness(8);

    viewer.showOutline([
        "gearbox#1", "gearbox#1.0", "gearbox#1.1", "gearbox#1.2" // ...
    ]);
});
````