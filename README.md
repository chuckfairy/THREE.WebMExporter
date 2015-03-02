# THREE.WebMExporter
Using toDataURL for the Three.js domElement, compile a frame array of Webp images into a WebM video for use in [three.js](http://threejs.org). It is based on [Whammy](https://github.com/antimatter15/whammy). Thank you mrdoob, AlteredQualia, and all those who made this happen.

NOTE: the current raytracing renderer in the example is edited very slightly to add an event listener when the render is finished.

## How to use

```html
<script src="WebMExporter.js"></script>
<script>

//For webgl use the preserveDrawingBuffer flag must be true
var renderer = new THREE.WebGLRenderer({ preserveDrawingBuffer: true });

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

//Create output compile blob
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

### addRenderFrame( duration )
Will render using scene and camera then add the frame
Pass optional duration in milliseconds will default to fps

### addFrame( canvasOrWebP, duration )
Add a frame from a canvas element or WebP image
Pass optional duration in milliseconds

### compile( )
output a video WebM blob

### createObjectURL( blob )
create a video src URL for playing and exporting video

### setQuality( quality )
Set quality from 1-100.
Can also be set from quality property using int 0-1

### setSpeed( speed )
Set default speed passing in int in milliseconds

## Live Demos

### In Action

* http://chuckfairy.com/THREE.WebMExporter/examples/webgl.html
* http://chuckfairy.com/THREE.WebMExporter/examples/canvas.html
* http://chuckfairy.com/THREE.WebMExporter/examples/raytracing.html

### Videos

* http://chuckfairy.com/THREE.WebMExporter/videos/webgl.webm
* http://chuckfairy.com/THREE.WebMExporter/videos/canvas.webm
* http://chuckfairy.com/THREE.WebMExporter/videos/raytracing.webm

## What's next?

* Vorbis audio adding
* HTML page frames
* You tell me, leave an issue or request
