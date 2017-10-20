# Assigning types to objects

Each object in your viewer may be optionally assigned a type. Types are strings that mean something within the domain of your application. When using xeometry as an IFC viewer, for example, then types would likely be IFC element types.

When you have assigned types to your objects, then you can specify types as the targets for various xeometry methods.

### Examples

Assigning IFC types to two objects:

```javascript
viewer.setType("house#12", "IfcFlowController");
viewer.setType("house#23", "IfcFlowFitting");
```

Getting the type of an object:

```javascript
var type = viewer.getType("house#12");
```

Getting all types in the viewer:

```javascript
var types = viewer.getTypes();
```

Getting all objects of the given type \(see [_Querying Models and Objects_](queryingModelsAndObjects.md)\):

```javascript
var typeObjects = viewer.getObjects("ifcCurtainWall");
```

Making all objects transparent except for the given types \(see [_Transparency_](transparency.md)\):

```javascript
viewer.setOpacity(0.4);
viewer.setOpacity(["IfcFlowController", "IfcFlowFitting"], 1.0);
```

Flying the camera to fit all objects of the given types \(see [_Fitting things in view_](fittingThingsInView.md)\):

```javascript
viewer.viewFit(["IfcFlowController", "IfcFlowFitting"], function() {
    // Camera arrived
});
```

Getting collective boundary of all objects of the given types  \(see: [_Querying Boundaries_](queryingBoundaries.md)\):

```javascript
var objectsBoundary = viewer.getAABB(["IfcFlowController", "IfcFlowFitting"]);
```



