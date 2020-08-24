# Getting Started 
Most likely you will have already created your models with your favorite design software and are looking to either view them as an enhancement to your website or add them into a Babylon.js scene as part of the web game or app you are designing.
## Export
The simplest way to [export]() your scene is from within the playground. You can use the *.babylon* format or the *GLB* format.

Select tools from the inspector and choose which type to export.

![inspector](/img/campus/pgpartmenu.png)  
![Tools](/img/campus/export.png)

## Viewing
The *Viewer* extension is a script you can add to your website that allows models to be displayed. More on this soon.

## Import
When you put a model into a scene you are, in fact, loading it into a browser. As you will already know when you load anything into a website it is asynchronous. Before you can do anything with your models you need to know they have loaded. You can do this using the *ImportMeshAsync* method of the *SceneLoader*.

### File Type .BABYLON
```javascript
BABYLON.SceneLoader.ImportMeshAsync(model names, folder path, file name, scene);
```
The scene parameter is optional and will default to the current scene.  
Examples
```javascript
BABYLON.SceneLoader.ImportMeshAsync("", "/relative path/", myModels.babylon); //empty string all meshes
BABYLON.SceneLoader.ImportMeshAsync("model1", "/relative path/", myModels.babylon); //Name of model for one model
BABYLON.SceneLoader.ImportMeshAsync(["model1", "model2"], "/relative path/", myModels.babylon); //Array of model names
```
The above examples will import the models only and you will not be able to manipulate them. The method *ImportMeshAsync* uses promises to return a result. When the import has finished then you can deal with the returned result as follows
```javascript
BABYLON.SceneLoader.ImportMeshAsync("", "/relative path/", myModels.babylon).then((result) => {
    const model1 = result.meshes[1]; //meshes, an array of all imported meshes is one of the properties of the result object
    model1.position.x = 5;
    const model2 = scene.getMeshByName("model2");
    //Set to 0 is required if orientations will be set using rotation rather than rotationQuaternion
    model2.rotation = BABYLON.rotation.Zero(); 
    model2.rotation.y = Math.PI / 4;
});
```
The first two playground examples only import the named models. The last one imports all the models and the positions of the houses are changed.

https://www.babylonjs-playground.com/#YNEAUL#1

https://www.babylonjs-playground.com/#YNEAUL#2

https://www.babylonjs-playground.com/#YNEAUL#3


### File Type .GLB

https://www.babylonjs-playground.com/#YNEAUL#4