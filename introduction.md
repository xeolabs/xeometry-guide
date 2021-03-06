# Concept

A xeometry [Viewer](http://xeometry.org/docs/#viewer) is a JavaScript class that wraps [xeogl](http://xeogl.org) in a set of simple data-driven methods that focus on loading glTF models and manipulating their scene elements, to create cool 3D presentations on WebGL.

Being data-driven, the Viewer is able to track all your scene updates, and can save and load complete snapshots of its runtime state as JSON bookmarks.

The example below shows the gist of how to use xeometry. In this example, we're creating a viewer, positioning its camera, loading a glTF model of a reciprocating saw, rotating the model so we can see it from the side, then making the handle objects transparent, so that we can see the armature objects inside.

```javascript
var viewer = new xeometry.Viewer();

viewer.setEye([-130, -40, 350]);
viewer.setLook([-130, -40, 0]);

viewer.loadModel("saw", "ReciprocatingSaw.gltf", function () {
    viewer.setRotate("saw", [90, 0, 0]);
    viewer.setOpacity(["saw#3.1", "saw#3.2"], 0.5);
});
```

[![](assets/transparency.png)](http://xeolabs.com/xeometry/examples/#effects_transparency)

\[ [Run demo](http://xeolabs.com/xeometry/examples/#effects_transparency) \]

Once everything's looking how we want, we can save the viewer to a JSON bookmark.

```javascript
var bookmark = viewer.getBookmark();
```

Then we can load that bookmark again, perhaps even into a different viewer instance, to exactly restore that view \(see [_Bookmarking_](bookmarking.md) for more info\).

```javascript
var viewer2 = new xeometry.Viewer();
viewer2.setBookmark(bookmark, function() { /* Loaded */ });
```

So that's the general idea of xeometry: a viewer API that lets you delve into your glTF models and dynamically tweak bits and pieces, while being totally data-driven,  which lets you save and load your changes.

See [Features](/features.md) for an overview of the things that you can do through the xeometry API.

