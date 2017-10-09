# Web-based model visualization with xeometry

xeometry is an open source JavaScript API from [@xeographics](https://www.gitbook.com/book/xeolabs/xeometry/edit#) for
viewing glTF models on WebGL.

> * [http://xeolabs.com/xeometry](xeolabs.com/xeometry)
> * [http://xeolabs.com/xeometry/examples](Examples)
> * [http://xeolabs.com/xeometry/examples](GitGub)
> * [http://xeolabs.com/xeometry/examples](MIT License)

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


Once you've loaded models and tweaked everything to make it look nice, you can dump the whole viewer state to
a JSON bookmark. You can then load that bookmark, perhaps into a different viewer instance, to exactly restore
that view (see [Viewer bookmarks](viewerBookmarks.md)).

````javascript
var bookmark = viewer.getBookmark();

var viewer2 = new xeometry.Viewer();
viewer2.setBookmark(bookmark, function() { /* Loaded */ });
````


Some things you can do through the xeometry API:

| Function | Pages |
|-- | -- |
| **load multiple 3D glTF 2.0 models into a viewer** | [Loading models](loadingModels.md) |
| **create multiple viewers in a page** | [Creating a viewer](creatingAViewer.md) |
| **show and hide objects** | [Showing and hiding objects](showingAndHidingObjects.md) |
| **make objects transparent** | see: [Making objects transparent](makingObjectsTransparent.md) |
| **translate, rotate and scale objects** | [Transforming models and objects](transformingModelsAndObjects.md) |
| **animate the camera** | [Controlling the camera](controllingTheCamera.md), [Panning the camera](panningTheCamera.md), [Rotating the camera](rotatingTheCamera.md) and [Zooming the camera](zoomingTheCamera.md) |
| **move camera to fit things in view** | [Fitting things in view](fittingThingsInView.md) |
| **create annotations** | [Creating annotations](creatingAnnotations.md) |
| **create custom clip planes | [Creating clip planes](creatingClipPlanes.md) |
| create light sources | [Creating light sources](creatingLightSources.md) |
| draw outlines around objects to emphasise them | [Outlining objects](outliningObjects.md) |
| save and load JSON bookmarks of viewer state | [Viewer bookmarks](viewerBookmarks.md) |
| dynamically query boundaries of models and objects | [Querying boundaries](queryingBoundaries.md) |
| dynamically query geometry of objects | [Querying object geometries](queryingObjectGeomatries.md) |
| pick objects with canvas coordinates or 3D ray | [Picking objects](picking.md) |
| take canvas snaphots | [Canvas snapshots](canvasSnapshots.md) |
| assign types (eg. IFC) to objects, so that types can be used instead of IDs when when specifying objects to viewer methods | [Assigning types to objects](assigningTypesToObjects.md) |

There are bound to be some things the API doesn't do for you. If those are within the scope of viewing and manipulating glTF content, then please [log the issue](TODO) for discussion.






