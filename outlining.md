# Outlining

You can emphasize objects in your viewer by displaying outlines around them.

### Example

````javascript
var viewer = new xeometry.Viewer();

viewer.setEye([-130, -40, 350]);
viewer.setLook([-130, -40, 0]);

viewer.setOutlineColor([1, 1, 0]);
viewer.setOutlineThickness(8);

viewer.loadModel("gearbox", "GearboxAssy.gltf", function () {
    viewer.showOutline([
        "gearbox#1", "gearbox#1.0", "gearbox#1.1", "gearbox#1.2" // ...
    ]);
});
````

[![](assets/outlining.png)](http://xeolabs.com/xeometry/examples/#guidebook_outlining)

Outlining all objects in a given model:

```javascript
viewer.hideOutline();
viewer.showOutline("saw");
```

Outlining the given types (see *[Assigning types to objects](assigningTypesToObjects.md)*):

```javascript
viewer.hideOutline();
viewer.showOutline(["IfcFlowController", "IfcFlowFitting"]);
```

