# Introduction

A xeometry [Viewer](http://xeolabs.com/xeometry/docs/#viewer) is a single class that wraps a [xeogl](http://xeogl.org)
3D engine in a set of simple data-driven methods focused on loading glTF models and manipulating scene content to create
cool presentations.

The example below shows the idea. In this example, we're loading a glTF model of a reciprocating saw, setting some objects
transparent to reveal the inner workings, then positioning the camera to fit everything in view.

[![](http://xeolabs.com/xeometry/assets/sawObjects.png)](http://xeolabs.com/xeometry/examples/#effects_opacity)

````javascript
var viewer = new xeometry.Viewer({ canvasId: "theCanvas" });

viewer.loadModel("saw", "models/Reciprocating_Saw.gltf", function () {
     viewer.setOpacity(["saw#0", "saw#1", "saw#2", "saw#3", "saw#11"], 0.3);
     viewer.viewFit("saw");
});
````

Viewer methods generally get or set some property of a target element in the scene, such as the opacity of an object, or
the position of the camera.

Some of the things you can do with objects are:

* showing and hiding,
* rotating, scaling and translating,
* changing opacity,
* annotating,
* outlining,
* slicing with clipping planes,
* getting boundaries,
* fitting to view,
* picking and raycasting.

xeometry tracks all your updates, and is able to serialize a viewer's state as a JSON bookmark:

````javascript
var bookmark = viewer.getBookmark();
````
A bookmark contains a complete snapshot of the viewer's state, including what models are loaded, object properties,
camera position etc - everything you've done through the viewer API. We can restore a viewer to a bookmark at any time:

````javascript
viewer.setBookmark(bookmark);
````

We can also initialize another viewer from a bookmark:

````javascript
var viewer2 = new xeometry.Viewer({ canvasId: "anotherCanvas" });
viewer2.setBookmark(bookmark);
````
