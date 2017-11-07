# Clipping

When you need to look inside your models, you can slice them open with custom clipping planes. These are defined in World space,
as a 3D position and a direction vector. Everything that falls in front of that position, in the direction of the vector,
will not be rendered, unless configured to be unclippable.

When you create a clip plane, you assign it a unique ID so that you can find it again within your viewer.

To see your clipping planes, you can set set them visible, which renders helper objects to show their
position and orientation, as shown in the example below.

The maximum number of clipping planes that xeometry supports is only limited by your system's WebGL support (namely the
number of _varying_ types supported in shaders). As of writing this, you should be OK with a maximum of six planes on
the lowest-end WebGL systems.

Another way to reveal interior objects is by making the outer objects transparent - see [_Transparency_](transparency.md).

### Example

In the example below, we'll position the camera and create a clipping plane that passes through the World-space origin
and discards everything on the +Z side. Then we'll load a glTF model of a reciprocating saw. Once that's loaded, we'll
rotate it 90 degrees, so we can view it from the side, and set two objects unclippable.  which will get sliced in half by
our clipping  plane, to reveal some of its inner workings.

````javascript
var viewer = new xeometry.Viewer();

viewer.setEye([-130, -40, 350]);
viewer.setLook([-130, -40, 0]);

viewer.createClip("clip1", {
    pos: [0, 0, 0],
    dir: [0, 0, -1]
});

viewer.loadModel("saw", "ReciprocatingSaw.gltf", function () {
    viewer.setRotate("saw", [90, 0, 0]);
    viewer.setUnclippable(["saw#3.4", "saw#3.2", "saw#3.4"]);
});
`````

[![](assets/clipping.png)](http://xeolabs.com/xeometry/examples/#guidebook_clipping)

For here, we can dynamically set and get all the properties of our clip planes (except for their IDs).

Getting and setting the position of a clip plane:

````javascript
viewer.setClipPos("clip1", [80, 0, 0]);
var pos = viewer.getClipPos("clip1");
// Returns [80,0,0]
````

Getting and setting the direction of the clip plane:

````javascript
viewer.setClipDir("clip1", [0, 1, 0]);
var dir = viewer.getClipDir("clip1");
// Returns [0,1,0]
````

Showing and hiding a clip plane's helper which indicates its position and orientation:

````javascript
viewer.showClip("clip1");
viewer.hideClip("clip1");
// Returns [0,1,0]
````

