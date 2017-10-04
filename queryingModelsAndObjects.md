# Querying models and objects

You can query the models and objects that are currently loaded in your viewer.

The ID of each object is prefixed by the ID of its model, ie. "&lt;model ID&gt;#&lt;object ID&gt;". Each object
corresponds to a ````node```` element within its model's glTF file. If the ````node```` has a ````name```` attribute,
then that's used for the object part of the ID, eg. "saw#outerCasing". Otherwise, the index of the ````node```` within
the flTF file's ````nodes```` section is used, eg. "saw#23".

Get all models:
````javascript
var models = viewer.getModels();
````

Get all objects:
````javascript
var objects = viewer.getObjects();
````

Get all objects in a model:
````javascript
var saw = viewer.getObjects("saw");
````

Get an object's model:
````javascript
var model = viewer.getModel("saw#23");
````