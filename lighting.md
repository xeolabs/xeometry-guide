# Lighting

xeometry lets you create and animate an unlimited number of custom light sources.

Light sources come in three types:

 * _"ambient"_ - ambient light source with _color_ and _intensity_,
 * _"point"_ - positional light source with _color_, _pos_, _intensity_,  plus _constantAttenuation_, _linearAttenuation_ and _quadraticAttenuation_,
 * _"dir"_ - directional light source with _color_, _dir_ and _intensity_

The _color_ properties are RGB, with each component having range ````[0..1]````. The _intensity_ property is a scaling factor in range ````[0..1]```, which governs how much each light source contributes to overall illumination. The and _pos_and _dir_ properties are World-space 3D position and direction, respectively.

The attenuation properties for _point_ lights determine how light intensity decreases in proportion to distance from _pos_.

The number of light sources is actually limited by your GPU, but you can safely have at least four or five directional
or point light sources on the lowest-end WebGL-compatible GPUs.

## Examples

Removing all light sources:

````javascript
viewer.destroyLights();
````

Creating custom ambient, directional and point lights:

````javascript
// Create a green ambient light
viewer.createLight("myAmbientLight", {
    type: "ambient",
    color: [0.6, 1.0, 0.6],
    intensity: 0.7
});

// Create a red directional light shining down the -Z axis
viewer.createLight("myDirLight", {
    type: "dir",
    color: [1.0, 0.5, 0.5],
    dir: [0,0,-1],
    intensity: 0.7
});

// Create a blue point light
viewer.createLight("myPointLight", {
    type: "pos",
    color: [0.5, 0.5, 1.0],
    pos: [1,1,-1],
    intensity: 1.0
});
````

Getting the IDs of the lights in your viewer:

```javascript
var lights = viewer.getLights();
// Returns ["myAmbientLight", "myDirLight", "myPointLight"]
```

Changing the color of the ambient light to yellow, while reducing its intensity:

```javascript
viewer.setColor("myAmbientLight", [1, 1, 0]);
viewer.setIntensity(0.4);
```

Changing the direction of the directional light, to make it shine downwards:

```javascript
viewer.setDir("myDirLight", [0, -1, 0]);
```

Changing the position of the point light:

```javascript
viewer.setDir("myPointLight", [-1, -1, 0]);
```

Note that xeometry will ignore (but log) attempts to set properties that don't exist on the target light source. For example,
if you try to set the direction of an ambient light, like so:

```javascript
viewer.setDir("myAmbientLight", [1, -1, 1]);
```

then xeometry will ignore the call and log a warning.

Find out more about light sources in the [API docs](http://xeometry.org/docs).