# Viewer bookmarks

You can save and load complete snapshots of viewer state as JSON bookmarks. A bookmark contains all the viewer's state, including:

* models loaded,
* object visibilities, opacities, outlines and types
* model and object transforms
* camera position and projection
* annotations
* clipping planes
* light sources
* outline appearance

### Example

In the example below, we're creating a viewer, positioning the camera, loading a glTF model of a reciprocating saw, then hiding some objects, to reveal the inner workings.

[![](http://xeolabs.com/xeometry/assets/sawObjects.png)](http://xeolabs.com/xeometry/examples/#effects_opacity)

```javascript
var viewer = new xeometry.Viewer();

viewer.setEye([-110.89, 0, 456.67]);
viewer.setLook([-110.89, 0, 44.85]);

viewer.loadModel("saw", "./ReciprocatingSaw.gltf", function () {
    viewer.setRotate("saw", [90, 0, 0]);
    viewer.hide(["saw#1.1", "saw#1.2"]);
});
```

#### Saving to a bookmark

We'll now save the state of our viewer to a bookmark:

````javascript
var bookmark = viewer.getBookmark();
````

The bookmark will look like this:

````json
{
	"models": [
		{
			"id": "saw",
			"src": "./ReciprocatingSaw.gltf",
			"rotate": [90,0,0]
		}
	],
	"objects": [
		{
			"id": "saw#1.1",
			"visible": false
		},
		{
			"id": "saw#1.2",
			"visible": false
		}
	],
	"lookat": {
		"eye": [-110.89,0,456.67],
		"look": [-110.89,0,44.85],
		"up": [0,1,0]
	}
}
````

For compactness, a bookmark only saves state that differs from the defaults. Therefore, our bookmark only saved the
updates that we programmed, such as the camera position, the model we loaded, its rotation, and the two hidden objects.

#### Loading the bookmark

We can now load the bookmark back into our viewer, or into a different viewer, to restore the scene that we
created programmatically earlier.

```javascript
viewer.setBookmark(bookmark, function() { /* Loaded */ });

var viewer2 = new xeometry.Viewer();
viewer2.setBookmark(bookmark, function() { /* Loaded */ });
```

