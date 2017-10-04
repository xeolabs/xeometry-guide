# Outlining objects

You can emphasize objects in your viewer by displaying outlines around them.

[![](assets/outlining.png)](http://xeolabs.com/xeometry/examples/#effects_outlining)

````javascript
var viewer = new xeometry.Viewer();

viewer.setEye([15, 0, -20]);
viewer.setLook([0, 0, 0]);

viewer.loadModel("gearbox", "GearboxAssy.gltf", function () {

    viewer.viewFit();

    viewer.setOutlineColor([1, 1, 0]);
    viewer.setOutlineThickness(8);

    viewer.showOutline([
        "gearbox#1", "gearbox#1.0", "gearbox#1.1", "gearbox#1.2", "gearbox#1.3",
        "gearbox#1.4", "gearbox#1.5", "gearbox#1.6", "gearbox#1.7", "gearbox#1.8", "gearbox#1.9"
    ])
});

new xeometry.CameraControl(viewer);
````