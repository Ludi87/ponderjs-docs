# PonderJS Docs

## Getting Started

### Ponder Tags

#### Creating a Tag

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

<details>
<summary>Example</summary>
<br>

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

</details>


