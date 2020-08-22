# Getting Started Page 7
## Copies
The two main ways to copy a mesh is to clone it or create an instance of it. Cloning gives you an independent copy of a mesh whereas an instance is still linked to the original for its material. You cannot change the material of an instance of a mesh. There are also advanced ways of creating copies which are available in the *Mesh Chapter*

To clone the house use

```javascript
clonedHouse = house.clone("clonedHouse")
```
and for an instance it is
```javascript
instanceHouse = house.createInstance("instanceHouse")
```

As at this point in our world all the houses will use the same material we will go with *createInstance*.

Before we do that we combine the building functions to produce a house of width 1 or 2.

https://www.babylonjs-playground.com/#KBS9I5#21

We will enlarge the ground and increase the camera radius a little to fit several house on and be able to view them.

After determining the positions for the houses we will use a loop to create them.

```javascript
const houses = [];

for (let i = 0; i < places.length; i++) {
    houses[i] = buildHouse(places[i][0]);
    houses[i].rotation.y = places[i][1];
    houses[i].position.x = places[i][2];
    houses[i].position.z = places[i][3];
}
```

https://www.babylonjs-playground.com/#KBS9I5#22

![Village 1](/img/campus/village1.png)

