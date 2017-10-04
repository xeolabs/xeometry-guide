# Picking objects

You can select objects by picking or raycasting. Picking involves finding objects at given canvas coordinates,  
while raycasting involves finding objects that intersect an arbitrarily-positioned World-space ray.

For both of these, you have the option of getting either just the object, or the object plus information  
about the 3D point that you've picked or raycasted on its surface.

---

Picking the object at the given canvas coordinates:

```javascript
var hit = viewer.pickObject([234, 567]);
if (hit) {
    console.log("object picked: " + hit.id);
}
```

Picking a point on the surface of an object, at the given canvas coordinates:

```javascript
hit = viewer.pickSurface([234, 567]);
if (hit) {
    var worldPos = hit.worldPos;
    console.log("object picked: " + hit.id);
    console.log("surface coordinates: " + worldPos[0] + "," + worldPos[1] + "," + worldPos[2]);
}
```

Getting the object that intersects a ray:

```javascript
hit = viewer.rayCastObject([0,0,-100], [0,0,1]); // Origin, dir
if (hit) {
    console.log("object raycasted: " + hit.id);
}
```

Getting object and point of surface intersection with a World-space ray:

```javascript
hit = viewer.rayCastSurface([0,0,-100], [0,0,1]); // Origin, dir
if (hit) {
    var worldPos = hit.worldPos;
    console.log("object raycasted: " + hit.id);
    console.log("surface coordinates: " + worldPos[0] + "," + worldPos[1] + "," + worldPos[2]);
}
```



