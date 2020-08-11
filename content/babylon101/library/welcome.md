# Getting Started Chapter 
## Welcome
Welcome to the wonderful 3D world of Babylon.js. Instead of the usual 'Hello World' introduction we will build a simple world, step by step, demonstrating the facilities of Babylon.js. All you need is a [scene]() to contain the world, a [camera]() to view it, a [light]() to illuminate it and at least one viewable object. All viewable objects, whether just a box or a complex character, are made from a [mesh]() of triangles or facets.

![wireframe](/img/campus/wireframe.png)  
Wireframe View Showing Mesh Triangles

After working through the first level and gaining a basic understanding of the possibilities with babylon.js the documentation has a wide range of tutorials to take you from level to level so we can build better worlds and you, your own worlds.

All you need to start coding with Babylon.js is a working knowledge of JavaScript. The [Babylon.js Playground](), or just playground, allows us to present examples within the documentation for you to follow, explore and edit. Of course, at some stage you will want to [publish]() your own code and following the template of the playground code gives you an easy way to transfer code back and forth between the two.

## Say Hello to Your First World

A simple box mesh is where we start after we use the Babylon.js Engine to set the scene, add a camera and light.

```javascript
const scene = new BABYLON.Scene(engine);

const camera = new BABYLON.ArcRotateCamera("camera", -Math.PI / 2, Math.PI / 2.5, 3, new BABYLON.Vector3(0, 0, 0), scene);
camera.attachControl(canvas, true);

const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(0, 1, 0), scene);

const box = BABYLON.MeshBuilder.CreateBox("box", {}, scene);
```

Like most meshes created with MeshBuilder the box is created positioned with its center at the origin and needs three parameters. These are a name, *a string*,  options, *a JavaScript object*, and a scene. By leaving the options with no properties the box defaults to one of unit size for its width, height and depth. 

To be usable in a playground we need to place these within a function called **createScene** which has to return a scene. The playground app takes care of the rest.

```javascript
const createScene =  () => {
    const scene = new BABYLON.Scene(engine);

    const camera = new BABYLON.ArcRotateCamera("camera", -Math.PI / 2, Math.PI / 2.5, 3, new BABYLON.Vector3(0, 0, 0));
    camera.attachControl(canvas, true);

    const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(0, 1, 0));

    const box = BABYLON.MeshBuilder.CreateBox("box", {});

    return scene;
}
```

Since at this point there is only one scene you may notice that this parameter can be dropped from the camera, light and box as the default is for them to be placed in the current scene.

https://www.babylonjs-playground.com/#KBS9I5


For the moment we will concentrate on creating the parts of the world you can see rather than the scene, camera and light.

[Next](/babylon101/ground) Grounding the world (meshes 1A).
