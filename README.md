# Web-based model visualization with xeometry

xeometry is an open source JavaScript API from [@xeographics](https://www.gitbook.com/book/xeolabs/xeometry/edit#) for
viewing glTF models on WebGL.

* [http://xeolabs.com/xeometry](xeolabs.com/xeometry)
* [http://xeolabs.com/xeometry/examples](Examples)
* [http://xeolabs.com/xeometry/examples](GitGub)
* [http://xeolabs.com/xeometry/examples](MIT License)

## Introduction

A xeometry [Viewer](http://xeolabs.com/xeometry/docs/#viewer) is a single class that wraps the WebGL-based [xeogl](http://xeogl.org)
3D engine in simple data-driven methods that are focused on loading glTF models and manipulating scene elements to create cool presentations.

The example below shows the general idea. In this example, we're positioning the camera, loading a glTF model (a reciprocating saw),
making the handle objects transparent to reveal the inner workings.

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

Some of the things you can do through the viewer API are:

* show and hide objects - (see [Viewer bookmarks](viewerBookmarks.md)),
* transform models and objects - (see [Transforming models and objects](transformingModelsAndObjects.md)),
* control object opacities - (see [Making objects transparent](makingObjectsTransparent.md)),
* create annotations - (see [Creating annotations](creatingAnnotations.md)),
* create outlines around objects - ,
* create arbitrary clipping planes -,
* query boundaries -,
* fit objects in view - ,
* pick and raycast objects - .

Once you've loaded models and tweaked everything to make it look nice, you can dump the whole viewer state to
a JSON bookmark. You can then load that bookmark, perhaps into a different viewer instance, to exactly restore
that view (see [Viewer bookmarks](viewerBookmarks.md)).

````javascript
var bookmark = viewer.getBookmark();

var viewer2 = new xeometry.Viewer();
viewer2.setBookmark(bookmark, function() { /* Loaded */ });
````






