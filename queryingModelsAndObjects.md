# Querying Models and Objects

You can query the IDs of the models and objects that are currently loaded in your viewer. You can then use those IDs to access the models and objects, to do things like query their boundaries or set their visibilities. 

The ID of each object is prefixed by the ID of its model, for example: "&lt;model ID&gt;\#&lt;object ID&gt;".

Each object corresponds to a `node` element within its model's glTF file. If the `node` has a `name` attribute, then that's used for the object part of the ID, eg. "saw\#outerCasing". Otherwise, the index of the `node` within the flTF file's `nodes` section is used, eg. "saw\#23".

### Examples

Getting all models in a viewer:

```javascript
var modelIds = viewer.getModels();
// Eg. ["saw", "gearbox"]
```

Getting all objects in a viewer:

```javascript
var objectIds = viewer.getObjects();
```

Get all objects in a model:

```javascript
var sawObjectIDs = viewer.getObjects("saw");
```

Get an object's model:

```javascript
var modelId = viewer.getModel("saw#23");
```

Get all objects of the given types \(see [_Assigning types to objects_](assigningTypesToObjects.md)\):

```javascript
var flowObjectIds = viewer.getObjects(["IfcFlowController", "IfcFlowFitting"]);
```



