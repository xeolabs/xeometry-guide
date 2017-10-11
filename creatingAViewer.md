# Creating a Viewer

Your first step is to link to the xeometry [library](http://xeolabs.com/xeometry/build/xeometry.min.js):

```html
<script src="xeometry.js"></script>
```

To create a viewer with a default internally-created canvas that fills the page:

```javascript
var viewer = new xeometry.Viewer();
```

To create a viewer with an existing canvas:

```javascript
var viewer = new xeometry.Viewer({
    canvasId: "myCanvas"
});
```

Note that you can create multiple viewers in the same page.

To destroy a viewer:

```javascript
viewer.destroy();
```



