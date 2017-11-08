# Querying Models and Objects

This page describes how to find the IDs of the models and objects that you have loaded in your viewer. Once you have those IDs, you can then access properties of the models and objects, to do things like [query their boundaries](queryingBoundaries.md) or [set their visibilities](visibility.md).

As described in [_Loading Models_](loadingModels.md), when we load a model, we assign it a unique ID. Each object loaded  in the model also gets a unique ID that's prefixed by the model's ID, Eg. _"&lt;model ID&gt;\#&lt;object ID&gt;"_.  This lets us load multiple copies of the same models, without getting ID conflicts between the objects.

Each object corresponds to a _node_ element within its model's glTF file. If the _node_ has a _name_ attribute, then that's used for the object part of the ID, eg. "saw\#outerCasing". Otherwise, the index of the _node_ within the glTF file's _nodes_ section is used, eg. "saw\#23".

### Examples

Getting the IDs of all models in a viewer:

```javascript
var modelIds = viewer.getModels();
// Eg. ["saw", "house"]
```

Getting all objects in a viewer:

```javascript
var objectIds = viewer.getObjects();
// Eg. ["saw#1", "saw#1.2", "saw#2", "house#12", "house#23", ...]
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
// Returns "saw"
```

Getting all objects of the given types \(see [_Assigning types to objects_](assigningTypesToObjects.md)\):

```javascript
var flowObjectIds = viewer.getObjects(["IfcFlowController", "IfcFlowFitting"]);
// Eg. ["house#12", "house#23"]
```



