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

As at this point in our world all the houses will use the same material we will go with *createInstance*