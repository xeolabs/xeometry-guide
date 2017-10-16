# Visibility

You can independently show and hide each object in your viewer. 

### Example

In the example below, we'll load a glTF model of a reciprocating saw, then hide a couple of its panel objects to reveal its inner workings.

```
var viewer = new xeometry.Viewer();

viewer.setEye([-130, -40, 350]);
viewer.setLook([-130, -40, 0]);

viewer.loadModel("saw", "ReciprocatingSaw.gltf", function () {
    viewer.setRotate("saw", [90, 0, 0]);
    viewer.hide(["saw#3.1", "saw#3.2"]);
});
```

[![](assets/visibility.png)](http://xeolabs.com/xeometry/examples/#guidebook_visibility)

### More examples

Showing everything in the viewer:

```javascript
viewer.show();
```

Hiding everything in the viewer:

```javascript
viewer.hide();
```

Show all objects within a model:

```javascript
viewer.show("saw");
```

Hiding all objects within our model:

```javascript
viewer.hide("saw");
```

Showing the given objects:

```javascript
viewer.show(["saw#3.1", "saw#3.2"]);
```

Showing all objects of the given types \(see [_Assigning types to objects_](assigningTypesToObjects.md)\):

```javascript
viewer.show(["IfcFlowController", "IfcFlowFitting"]);
```

Showing a model and two objects:

```javascript
viewer.show(["saw", "saw#3.1", "saw#3.2"]);
```

Hiding a model, two objects and all objects of the given type:

```javascript
viewer.hide(["saw", "gearbox#1", "gearbox#5", "IfcFlowFitting"]);
```



