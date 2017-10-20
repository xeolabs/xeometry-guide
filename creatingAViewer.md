# Creating a Viewer

Your first step is to link to the xeometry [library](http://xeolabs.com/xeometry/build/xeometry.min.js):

```html
<script src="xeometry.js"></script>
```

Creating a viewer with a default canvas, that fills the page:

```javascript
var viewer = new xeometry.Viewer();
```

Creating a viewer bound to an external canvas:

```javascript
var viewer = new xeometry.Viewer({
    canvasId: "myCanvas"
});
```

You can create multiple viewers in the same page.

To destroy a viewer:

```javascript
viewer.destroy();
```

Your next step is to load a model into a viewer- see [_Loading Models._](https://www.gitbook.com/book/xeolabs/xeometry/edit#)

