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

[![](assets/transparency.png)](http://xeolabs.com/xeometry/examples/#guidebook_transparency)

````javascript
var viewer = new xeometry.Viewer();

viewer.setEye([-145.22, -32.97, 282.5]);
viewer.setLook([-147.68, -20.64, 0]);
viewer.setUp([0, 1, 0]);

viewer.loadModel("saw", "ReciprocatingSaw.gltf", function () {
    viewer.setRotate("saw", [90, 0, 0]);
    viewer.setOpacity(["saw#1", "saw#1.28", "saw#1.1"], 0.3);
});
````

If we then save our viewer to a bookmark:

````javascript
var bookmark = viewer.getBookmark();
````

the bookmark will look this:

````JSON
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
			"id": "saw#1",
			"opacity": 0.3
		},
		{
        	"id": "saw#1.28",
        	"opacity": 0.3
       	},
        {
        	"id": "saw#1.1",
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

For compactness, a bookmark only saves state that differs from the defaults. Therefore, our bookmark only saved the
updates that we programmed, such as the camera position, the model we loaded, its rotation, and the two hidden objects.

We can now load the bookmark back into our viewer, or into a different viewer, to restore the scene that we
created programmatically earlier.

```javascript
viewer.setBookmark(bookmark, function() { /* Loaded */ });

var viewer2 = new xeometry.Viewer();
viewer2.setBookmark(bookmark, function() { /* Loaded */ });
```

