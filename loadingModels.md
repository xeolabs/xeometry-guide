# Loading Models

You can load multiple glTF 2.0 models into a viewer at the same time, as well as multiple copies of the same model.

#### Supported glTF features

xeometry only loads geometries, materials and transforms from glTF, without animations, cameras or lights.

#### Model and object IDs

When you load a model, you assign it a  unique ID so that you can find it within the viewer. That ID will get
prefixed to the IDs of the model's objects. This allows two or more copies of the same model to be loaded at the
same time, without ID clashes between their objects. See *[Querying Models and Objects](queryingModelsAndObjects.md)*
for querying the IDs of the objects within your loaded models.

### Examples

Loading two separate models into a viewer:

```javascript
viewer.loadModel("saw", "./Reciprocating_Saw.gltf", function () {
    // Loaded
 });

viewer.loadModel("gearbox", "./GearboxAssy.gltf", function () {
    // Loaded
});
```

Loading two copies of the same model into a viewer:

```javascript
viewer.loadModel("saw1", "./Reciprocating_Saw.gltf",  function () {
    // Loaded
});

viewer.loadModel("saw2", "./Reciprocating_Saw.gltf",  function () {
    // Loaded
});
```

Fly the camera to look at one of our models (see *[Fitting things in view](fittingThingsInView.md)*):

```javascript
viewer.viewFit("gearbox", function() {
    // Camera arrived
});
```

Get IDs of all models currently loaded (see *[Querying Models and Objects](queryingModelsAndObjects.md)*):

```javascript
var models = viewer.getModels();
```

Get IDs of objects in one of our models (see *[Querying Models and Objects](queryingModelsAndObjects.md)*):

```javascript
var saw = viewer.getObjects("gearbox");
```

Get World-space boundary of one of our models (see *[Querying Boundaries](queryingBoundaries.md)*):

```javascript
var saw = viewer.getObjects("gearbox");
```

Unloading a model:

```javascript
viewer.unloadModel("gearbox");
```

Clearing everything from the viewer:

```javascript
viewer.clear();
```



