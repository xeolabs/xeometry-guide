# Querying Models and Objects

You can query the IDs of the models and objects that are currently loaded in your viewer. You can then use those IDs to access properties of the models and objects, to do things like [query their boundaries](queryingBoundaries.md) or [set their visibilities](visibility.md).

The ID of each object is prefixed by the ID of its model, for example: "&lt;model ID&gt;\#&lt;object ID&gt;". This allows us to load multiple copies of the same model without getting ID conflicts between the objects.

Each object corresponds to a _node_ element within its model's glTF file. If the _node_ has a _name_ attribute, then that's used for the object part of the ID, eg. "saw\#outerCasing". Otherwise, the index of the _node_ within the flTF file's _nodes_ section is used, eg. "saw\#23".

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



