# Annotations

An annotation is a labeled pin that's attached to the surface of an object.

An annotation is pinned within a triangle of an object's geometry, at a position given in barycentric coordinates. A  
barycentric coordinate is a three-element vector that indicates the position within the triangle as a weight per vertex,  
where a value of \[0.3,0.3,0.3\] places the annotation at the center of its triangle.

An annotation can be configured with an optional camera position from which to view it, given as eye, look and up vectors.

By default, an annotation will be invisible while occluded by other objects in the 3D view.

Note that when you pick an object with \#.Viewer\#rayCastSurface or \#.Viewer\#pickSurface, you'll get a triangle index and  
barycentric coordinates in the intersection result. This makes it convenient to create annotations directly from pick  
results.

### Example

In the example below, we'll position the camera and load a glTF model of a reciprocating saw. When the model has loaded, we'll rotate it so that we can see it from the side. Then we'll hide a couple of cover objects so that we can see the armature bearing, which is normally hidden inside the cover. Finally, we'll create annotations on the armature bearing and one of the bearing enclosures.

```javascript
var viewer = new xeometry.Viewer();

viewer.setEye([-296.56, 26.78, 300.49]);
viewer.setLook([-130, -40, 0]);
viewer.getUp([0.09, 0.98, -0.16]);

viewer.loadModel("saw", "ReciprocatingSaw.gltf", function () {

    viewer.setRotate("saw", [90, 0, 0]);

    viewer.hide(["saw#3.1", "saw#3.2"]);

    viewer.createAnnotation("a1", {
        object: "saw#3.32",
        primIndex: 3303,
        bary: [0.3333, 0.3333, 0.3333],
        glyph: "A1",
        title: "Armature Bearing",
        desc: "DeWalt Reciprocating Saw Ball Bearing 330003-09",
        eye: [-254.21, -20.34, 49.75],
        look: [-213.19, -20.63, -0.00],
        up: [-0.36, 0.81, 0.44],
        pinShown: true,
        labelShown: true,
        occludable: true
    });

    viewer.createAnnotation("a2", {
        primIndex: 11532,
        bary: [0.3333, 0.3333, 0.3333],
        glyph: "A2",
        title: "Bearing enclosure",
        desc: "Front bearing enclosure 330003-12",
        object: "saw#3.94",
        eye: [-107.94, -31.69, 101.03],
        look: [-103.53, -20.64, 0],
        up: [-0.03, 0.75, 0.66],
        pinShown: true,
        labelShown: true,
        occludable: true
    });
});
```

[![](assets/annotations.png)](http://xeolabs.com/xeometry/examples/#guidebook_annotations)

