# Annotations

An annotation is a labeled pin that's attached to the surface of an object.

[![](http://xeolabs.com/xeometry/assets/sawObjects.png)](http://xeogl.org/examples/#presentation_annotations_tronTank)

An annotation is pinned within a triangle of an object's geometry, at a position given in barycentric coordinates. A
barycentric coordinate is a three-element vector that indicates the position within the triangle as a weight per vertex,
where a value of [0.3,0.3,0.3] places the annotation at the center of its triangle.

An annotation can be configured with an optional camera position from which to view it, given as eye, look and up vectors.

By default, an annotation will be invisible while occluded by other objects in the 3D view.

Note that when you pick an object with #.Viewer#rayCastSurface or #.Viewer#pickSurface, you'll get a triangle index and
barycentric coordinates in the intersection result. This makes it convenient to create annotations directly from pick
results.

### Examples


