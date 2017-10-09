# Web-based model visualization with xeometry

xeometry is an open source JavaScript API from [@xeographics](https://www.gitbook.com/book/xeolabs/xeometry/edit#) for
viewing glTF models on WebGL.

> * [Website](http://xeolabs.com/xeometry)
> * [Examples](http://xeolabs.com/xeometry/examples)
> * [API Docs](http://xeolabs.com/xeometry/docs/)
> * [GitHub](https://github.com/xeolabs/xeometry)

## The Gist

A xeometry [Viewer](http://xeolabs.com/xeometry/docs/#viewer) is a single class that wraps the WebGL-based [xeogl](http://xeogl.org)
3D engine in a set of simple data-driven methods that focus on loading glTF models and manipulating scene elements to create cool 3D presentations.

The example below shows the general idea. In this example, we're positioning the camera, loading a model of a reciprocating saw,
rotating the model so we can see it from the side, then making the handle objects transparent to reveal the inner workings.

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


Once you've loaded your models and tweaked everything to make them look nice, you can dump the whole viewer state to
a JSON bookmark. You can then load that bookmark again, perhaps into a different viewer instance, to exactly restore
that view (see [Viewer bookmarks](viewerBookmarks.md)).

````javascript
var bookmark = viewer.getBookmark();

var viewer2 = new xeometry.Viewer();
viewer2.setBookmark(bookmark, function() { /* Loaded */ });
````


