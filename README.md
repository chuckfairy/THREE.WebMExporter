# THREE.WebMExporter
Using toDataURL for the Three.js domElement, compile a frame array of Webp images into a WebM video. It is based on [Whammy](https://github.com/antimatter15/whammy).

## How to use

```html

<script>

//For webgl use the preserverDrawingBuffer flag must be true
var renderer = new THREE.WebGLRenderer({ preserverDrawingBuffer: true });

//Exporter construct
var exporter = new THREE.WebMExporter({

    //Render options
    renderer: renderer,
    scene: scene,
    camera: camera,

    //speed in frames per second
    speed: 60,

    //Quality 1-100
    quality: 100

});

var numberOfFrames = 200;

for(var i = 0; i < numberOfFrames; i++) {

    exporter.addRenderFrame();

}

output = exporter.compile();
var url = exporter.createObjectURL(output);

video.src = url;

//Additionally you can add from addFrame method
renderer.render(scene, camera);
exporter.addFrame(renderer.domElement);


</script>
```
## Properties

### renderer
Three.js renderer for use in addRenderFrame

### scene
scene to render

### camera
camera to use for render


## Methods

### addRenderFrame
Will render using scene and camera then add the frame

### addFrame
Add a frame from a canvas element

### compile
output a video WebM blob

### createObjectURL
create a video src URL for playing and exporting video

## Live Demos
In Action > http://chuckfairy.com/THREE.WebMExporter/examples/webgl.html
Video > http://chuckfairy.com/THREE.WebMExporter/videos/webgl.webm
