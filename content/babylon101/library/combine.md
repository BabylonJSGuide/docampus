# Getting Started Page 7
## Combining Meshes Using Merge Meshes
This is a straight forwarded way of combining two or more meshes.

```javascript
const combined = BABYLON.Mesh.MergeMeshes(Array_of_Meshes_to_Combine)
```
In our case this would be
```javascript
const house = BABYLON.Mesh.MergeMeshes([box, roof])
```
https://www.babylonjs-playground.com/#KBS9I5#11

![house 5](/img/campus/house5.png)

The first thing we note is that the whole house is covered in only one of the material used. Fortunately this can be corrected using the multiMultiMaterial parameter of *MergeMeshes, unfortunately this is the final parameter of a long list. The code now looks like
```javascript
const house = BABYLON.Mesh.MergeMeshes([box, roof], true, false, null, false, true);
```
At this stage it is important to note that the second parameter being true disposes of the original meshes and the last parameter being true allows the original material to be applied separately to the parts matching the original meshes.

https://www.babylonjs-playground.com/#KBS9I5#11

![house 3](/img/campus/house3.png)

[Prev](/babylon101/face_materials) Apply Material to Different Faces.  
[Next](/babylon101/copies) Copying Meshes.

[Mesh Chapter](/how_to/how_to_merge_meshes) Merge Meshes.

