# Assigning types to objects

Each object in your viewer may optionally be assigned a type. Types are strings that mean something within  
the domain of your application. When using xeometry as an IFC viewer, for example, then types would likely  
 be IFC element types.

When you have assigned types to your objects, then you can specify types as the targets for various xeometry methods.

---

Assign types to two objects:

```javascript
viewer.setType("house#12", "IfcFlowController");
viewer.setType("house#23", "IfcFlowFitting");
```

Get the type of an object:

```javascript
var type = viewer.getType("house#12");
```

Get all types in the viewer:

```javascript
var types = viewer.getTypes();
```

Get all objects of the given type:

```javascript
var typeObjects = viewer.getObjects("ifcCurtainWall");
```



