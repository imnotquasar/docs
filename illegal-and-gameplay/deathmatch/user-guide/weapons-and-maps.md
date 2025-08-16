# Weapons and maps

To edit weapons and maps in **Quasar Deathmatch Creator**, you can modify the configuration files located in the **html/js/config/** directory. These files include **`guns.js`** for weapons and **`maps.js`** for the available maps. Below is a brief guide on how to modify these files.

***

## **Editing weapons** <a href="#editing-weapons" id="editing-weapons"></a>

In the guns.js file, you will find an array of objects representing different weapons. Each weapon is configured with attributes such as name, img, and type. To add or modify a weapon, simply adjust the object structure within this array.

Example snippet from guns.js:

```javascript
const guns = [
  {
    name: "Advanced Rifle",
    img: "advancedrifle.png",
    type: "rifle"
  },
  {
    name: "AP Pistol",
    img: "appistol.png",
    type: "pistol"
  },
];
```

Here, you can edit the name, provide the corresponding image in the **html/images/** folder, and categorize the weapon using the type field. You can add as many weapons as you'd like, following this format.

***

## Editing maps <a href="#editing-maps" id="editing-maps"></a>

Similarly, maps can be edited in the maps.js file. Each map is represented by an object with name and img fields. You can customize maps by adding or changing objects within this array.

Example snippet from `maps.js`:

```javascript
const maps = [
  {
    name: "Cargo",
    img: "cargo.png"
  },
  {
    name: "Bank",
    img: "bank.png"
  },
];
```

As with weapons, ensure that the image file for each map is stored in the **html/images/** folder and properly referenced by the img field.
