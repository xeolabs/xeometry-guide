# Canvas Snapshots

You can take a snapshot of your viewer, as a JPEG, PNG or BMP image.

Snapshots are taken asynchronously, since we need to wait for xeometry to render the next frame before we can snapshot it.

### Examples

Grab a PNG image of the canvas, scaled to 500x500 pixels, then showing the image in an HTML image element:

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

Grab a JPEG image of the canvas, scaled to 600x400 pixels, then showing the image in an HTML image element:

```javascript
var image = new Image();

viewer.getSnapshot({
    width: 600, 
    height: 400,
    format: "jpeg" 
}, function (imageData) {
    image.src = imageData;
});
```



