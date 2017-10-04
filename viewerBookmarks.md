# Viewer bookmarks

You can save and restore the state of a viewer as a JSON bookmark. A bookmark contains all the viewer's state, including:

* models loaded,
* object visibilities, opacities, outlines and types
* model and object transforms
* camera position and projection
* annotations
* clipping planes
* outline appearance

---

Save model state to JSON bookmark, clear model then restore it again from the bookmark:

```javascript
var json = viewer.getBookmark();
viewer.reset();
viewer.setBookmark(json, function() { /* Loaded */ });
```



