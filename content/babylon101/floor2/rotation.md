1.1.2.1B2
# Rotation
Rotation in 3D space is always tricky. The order in which rotations are applied and the frame of reference used changes the final orientation of a mesh. There is a range of conventions for applying rotations in 3D modelling. For more details on these conventions in Babylon.js see [Applying Rotations Convention BJS](/resources/rotation_conventions).

To help in visualizing orientation this asymmetric mesh is used in examples

![The Pilot](/img/how_to/Mesh/pilot.jpg)

The most straight forward method to change the orientation of a mesh is the rotation property.

```javascript
 mesh.rotation = new BABYLON.Vector3(alpha, beta, gamma);
``` 
or

```javascript
mesh.rotation.x  =  alpha; //rotation around x axis
mesh.rotation.y  =  beta;  //rotation around y axis
mesh.rotation.z  =  gamma; //rotation around z axis
```
where alpha, beta, and gamma are angles measured in radians.

Four questions need an immediate answer

1. Where is the center of rotation?
2. Are they applied in a clockwise or counter clockwise direction?
3. What is the frame of reference?
4. In which order are they applied?


The first two are easy to answer since the center of rotation is the local origin of the mesh and rotations are always counter clockwise when looking in the positive direction of the stated axis.

The answer to 4 depends on 3 and in Babylon.js the rotation frame of reference is in the local space of the mesh being rotated.
It makes no difference which one of the following four sets of code you use the resulting orientation will always be the same.  

```javascript
mesh.rotation = new BABYLON.Vector3(alpha, beta, gamma);

mesh.rotation.x  =  alpha;
mesh.rotation.y  =  beta;
mesh.rotation.z  =  gamma;

mesh.rotation.z  =  gamma;
mesh.rotation.x  =  alpha;
mesh.rotation.y  =  beta;

mesh.rotation.y  =  beta;
mesh.rotation.z  =  gamma;
mesh.rotation.x  =  alpha;
```
The order is - a rotation of beta about the local y axis, then alpha about the local x axis and finally a rotation of gamma about the local z axis.

The following sequence of images shows this order of rotation.  
Red x axis, green y axis, blue z axis.

![Local Rotation](/img/campus/rotateorder.png)

0 rotation &pi;/2 about y, then &pi;/2 about x, then &pi;/2 about z.


* [Playground Example - Positioned, Scaled, and Rotated Boxes](https://www.babylonjs-playground.com/#CURCZC)

## Sequencing Rotations

The question now is, what to do if you want a sequence of rotations that starts with one about the x axis, then about the y axis then about the z axis?

For **world axes** you use the [rotate method](/features/Position,_Rotation,_Scaling). For rotations about **local axes**, Babylon.js has both the _rotate_ method and _addRotation_ method. 

You can chain a sequence of rotations using the _addRotation_. This method provides for one rotation value about one axis a series of which can be applied from the first to the last as the following example shows.

```javascript 
mesh.addRotation(Math.PI/2, 0, 0).addRotation(0, Math.PI/2, 0).addRotation(0, 0, Math.PI/2);
```

The following sequence of images shows the result of adding the individual rotations one after the other for the above playground, starting with the initial position of the pilot followed by a rotation of &pi;/2 about the local x axis, then &pi;/2 about the local y axis and finally a rotation of &pi;/2 about the local z axis.

![Added Rotations](/img/babylon101/pilotA.jpg)

The smaller axes represent the direction of the **world axes**.

In general _mesh.addRotation(alpha, beta, gamma)_ needs at least two of _alpha, beta, gamma_ to be 0 where _alpha_ is a rotation about the local x axis, _beta_ about the local y axis and _gamma_ about the local z axis.

## RotationQuaternions
An alternative to _rotations are [_rotationQuaternions_](/resources/rotation_conventions#quaternions) though they can be tricky to use but can overcome some gimbal lock problems. Using both on a mesh is not possible see [warning](/resources/rotation_conventions#warning)

## Scaling

Scaling along the x, y, and z **local axes** is set using

```javascript
mesh.scaling = new BABYLON.Vector3(scale_x, scale_y, scale_z);
```
 or individually with

 ```javascript
 mesh.scaling.y = 5;
 ```

 The following image shows a unit cube rotated about the z axis and scaled along the local y axis.

 ![scaled](/img/babylon101/scaling1.jpg)


## Next step

Now you know how to create and move objects in a scene, but all your meshes have the same 'skin'. Not for long, if you read our next tutorial about [materials](/babylon101/materials).

# Further Reading

## Features

- [Rotate and Translate Overview](/features/Position,_Rotation,_Scaling)  


