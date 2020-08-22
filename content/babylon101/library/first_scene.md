# Getting Started Page 1
## First Scene and Model
To start to create our simple world all you need is a [scene]() to contain the world, a [camera]() to view it, a [light]() to illuminate it and at least one viewable object. All viewable objects, whether just a box or a complex character, are made from a [mesh]() of triangles or facets.

![wireframe](/img/campus/wireframe.png)  
Wireframe View Showing Mesh Triangles

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

[Next](/babylon101/ground) Grounding the world
