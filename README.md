# three-stereo-effect
A fork of the stereo effect for npm package

ThreeJS StereoEffect as an npm module. 

```js
var THREE = require('three')

var StereoEffect = require('three-stereo-effect')(THREE)

function start(gl, width, height) {
    renderer = new THREE.WebGLRenderer({
        canvas: gl.canvas
    })
    renderer.setClearColor(0x000000, 1.0)

    scene = new THREE.Scene()
    camera = new THREE.PerspectiveCamera(50, width/height, 1, 1000)
    camera.position.set(0, 1, -3)
    camera.lookAt(new THREE.Vector3())

    stereoEffect = new StereoEffect(renderer)
    stereoEffect.eyeSeparation = 1;
    stereoEffect.setSize( width, height );

    var geo = new THREE.BoxGeometry(1,1,1)
    var mat = new THREE.MeshBasicMaterial({ wireframe: true, color: 0xffffff })
    var box = new THREE.Mesh(geo, mat)
    scene.add(box)
}

function render(gl, width, height) {
    stereoEffect.render(scene, camera)
}
```


#### `StereoEffect = require('three-stereo-effect')(THREE)`

This module exports a function which accepts an instance of THREE, and returns an StereoEffect class. This allows you to use the module with CommonJS, globals, etc.


The returned function has the following constructor pattern:

```js
stereoEffect = new StereoEffect(renderer)
```
