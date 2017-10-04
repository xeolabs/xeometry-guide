# Loading models

You can load multiple glTF 2.0 models into a viewer at the same time, as well as multiple copies of the same model.

> **glTF support:** xeometry loads glTF 2.0 geometries, materials and modeling transform hierarchies, without animations.  
>  In addition to glTF's core  
> metallic material workflow, xeometry also supports specular and common materials. It does not  
> load cameras or lights because the viewer manages those globally, for all the models you load.



Loading two separate models into a viewer

```javascript
viewer.loadModel("saw", "./Reciprocating_Saw.gltf", function () {
    // Loaded
 });

viewer.loadModel("gearbox", "./GearboxAssy.gltf", function () {
    // Loaded
});
```

Loading two copies of the same model into a viewer

```javascript
viewer.loadModel("saw1", "./Reciprocating_Saw.gltf",  function () {
    // Loaded
});

viewer.loadModel("saw2", "./Reciprocating_Saw.gltf",  function () {
    // Loaded
});
```

\`Unloading a model

```javascript
viewer.unloadModel("gearbox");
```

Clearing everything from the viewer:

```javascript
viewer.clear();
```



