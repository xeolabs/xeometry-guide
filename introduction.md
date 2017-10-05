# Introduction

A xeometry [Viewer](http://xeolabs.com/xeometry/docs/#viewer) is a single class that wraps [xeogl](http://xeogl.org)
(a WebGL-based 3D engine) in simple data-driven methods focused on loading glTF models and manipulating their
objects to create cool presentations.

Once you've loaded models, arranged the camera, tweaked objects and so forth, you can save the state of your viewer to
a JSON bookmark object. You can then load that bookmark, perhaps into a different viewer instance, to exactly restore
that view.

The example below shows the idea. In this example, we're loading a glTF model of a reciprocating saw, setting some objects
transparent to reveal the inner workings, then positioning the camera to fit everything in view.

[![](http://xeolabs.com/xeometry/assets/sawObjects.png)](http://xeolabs.com/xeometry/examples/#effects_opacity)

```javascript
var viewer = new xeometry.Viewer();

viewer.setEye([-110.89, 0, 456.67]);
viewer.setLook([-110.89, 0, 44.85]);

viewer.loadModel("saw", "models/gltf/ReciprocatingSaw/glTF/ReciprocatingSaw.gltf", function () {
    viewer.setRotate("saw", [90, 0, 0]);
    viewer.setOpacity(["saw#1.1", "saw#1.2"], 0.3);
});
```

If we then save a bookmark:

````javascript
var bookmark = viewer.getBookmark();
````

it's going to look this:

````json
{
	"models": [
		{
			"id": "saw",
			"src": "models/gltf/ReciprocatingSaw/glTF/ReciprocatingSaw.gltf",
			"rotate": [90,0,0]
		}
	],
	"objects": [
		{
			"id": "saw#1.1",
			"opacity": 0.3
		},
		{
			"id": "saw#1.2",
			"opacity": 0.3
		}
	],
	"lookat": {
		"eye": [-110.89,0,456.67],
		"look": [-110.89,0,44.85],
		"up": [0,1,0]
	}
}
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

```javascript
var bookmark = viewer.getBookmark();
```

A bookmark contains a complete snapshot of the viewer's state, including what models are loaded, object properties,  
camera position etc - everything you've done through the viewer API. We can restore a viewer to a bookmark at any time:

```javascript
viewer.setBookmark(bookmark);
```

We can also initialize another viewer from a bookmark:

```javascript
var viewer2 = new xeometry.Viewer({ canvasId: "anotherCanvas" });
viewer2.setBookmark(bookmark);
```



