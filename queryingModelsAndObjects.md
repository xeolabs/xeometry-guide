# Querying Models and Objects

You can query the IDs of the models and objects that are currently loaded in your viewer. You can then use those IDs to access the models and objects, to do things like [query their boundaries](queryingBoundaries.md) or [set their visibilities](visibility.md).

The ID of each object is prefixed by the ID of its model, for example: "&lt;model ID&gt;\#&lt;object ID&gt;". This allows us to load multiple copies of the same model without getting ID conflicts between the objects.

Each object corresponds to a `node` element within its model's glTF file. If the `node` has a `name` attribute, then that's used for the object part of the ID, eg. "saw\#outerCasing". Otherwise, the index of the `node` within the flTF file's `nodes` section is used, eg. "saw\#23".

### Examples

Getting the IDs of all models in a viewer:

```javascript
var modelIds = viewer.getModels();
// Eg. ["saw", "gearbox"]
```

Getting all objects in a viewer:

```javascript
var objectIds = viewer.getObjects();
// Eg. ["saw#1", "saw#1.2", "saw#2", "gearbox#1", "gearbox#1.1", ...]
```

Note how each ID is prefixed with the ID of its object's model. 

Getting all objects in a model:

```javascript
var sawObjectIDs = viewer.getObjects("saw");
// Eg. ["saw#1", "saw#1.2", "saw#2", ...]
```

Getting an object's model:

```javascript
var modelId = viewer.getModel("saw#23");
```

Getting all objects of the given types \(see [_Assigning types to objects_](assigningTypesToObjects.md)\):

```javascript
var flowObjectIds = viewer.getObjects(["IfcFlowController", "IfcFlowFitting"]);
```



