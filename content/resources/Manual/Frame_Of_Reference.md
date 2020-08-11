# Transformation Chapter Page 8
## Frame of Reference

Every mathematical vector and transformation is expressed in a _frame of reference_ which is stored as a matrix.  In Babylon.js the data describing a mesh is stored as local space vectors. The _frame of reference_ for the mesh is determined by the world matrix for the mesh which is formed from any rotation, translation and scaling operations. For each rendered frame the current world matrix is used on the local space data to obtain the world data for the mesh.

The vertex data for a mesh on creation is stored and remains the same throught Babylon.js processing unless [baked](/resources/Baking_Transformations). As you position, translate, rotate and scale a mesh the world matrix for the mesh is updated to reflect these transformations. Before rendering each frame the world matrix is applied to the mesh vertex data to determine its world 3D data. However the frame of reference for the mesh to be viewed is a 2D screen and this frame of reference is a projection matrix which is applied to the mesh's world 3D data.

The world and projection matrix operations are carried out within the GPU (graphic processor unit) in a piece of code called the [vertex shader](/resources/shaderintro).


![World Matrix](/img/resources/world_matrix.jpg)

Though rarely needed you can set the vertex data of the mesh to its world 3D data and either reset the world matrix to the identity matrix or leave it be. This is done by [baking the transformation](/resources/Baking_Transformations) into the mesh.

[Prev](/how_to/transform_coordinates) Transform Coordinates  
[Next](/resources/baking_transformations) Baking Transformations