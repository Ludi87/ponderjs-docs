# PonderJS Docs

## Getting Started

## Ponder Tags

### Creating a Tag

Parameter   |   Description     | Example
---:        | :---              | :---
id          |   the tag name    |   "kubejs:getting_started"
displayItem |   the icon        |   "minecraft:paper"
title       |   the title       |   "Getting Started"
description |   the description |   "This is a description"
ingredient  |   default item(s) |   ["minecraft:paper", "minecraft:apple", ...]

```js
public void createTag(String id, ItemStackJS displayItem, String title, String description, IngredientJS ingredient)
```

```js
event.createTag(
    "kubejs:getting_started",   //id
    "minecraft:paper",          //displayItem
    "Getting started.",         //title
    "We ponder now!",           //description
    [    
        "minecraft:paper",          //ingredient
        "minecraft:apple",
        "minecraft:emerald_block",
    ]
);
```

## Type Syntax

In PonderJS some functions will need a selection, block position or a vector. The selection is an area between two positions or vectors.

KubeJS and PonderJS provide a simple syntax to pass a position or vector to a function.

Passing an array with three values `[x, y, z]` to a function that requires a selection, block position or vector will automatically wrap the array to the corresponding type.

If you want to shorthand a selection area you can pass in the following types:

* `[x1, y1, z1, x2, y2, z2]`
* `[vector1, vector2]`
* `[blockPos1, blockPos2]`
* `[[x, y, z], [x, y, z]]`

If you dislike the shorthand syntax, you can always use the functions provided in the `util` object in your Ponder scenes. You can read more about it here.
