# Canvas snapshots

You can take a snapshot of your viewer, as a JPEG, PNG or BMP image.

Snapshots are taken asynchronously.

### Examples

Grab a PNG image of the canvas, scaled to 500x500 pixels:

```javascript
var image = new Image();

viewer.getSnapshot({
    width: 500, // Defaults to size of canvas
    height: 500,
    format: "png" // Options are "jpeg" (default), "png" and "bmp"
}, function (imageData) {
    image.src = imageData;
});
```



