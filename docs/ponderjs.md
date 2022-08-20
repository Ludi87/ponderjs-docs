# PonderJS Docs

## Getting Started

### Ponder Tags

<details open>
<summary>Creating a Tag</summary>

```js
event.createTag(String id, ItemStackJS displayItem, String title, 
                String description, IngredientJS ingredient)
```

<details>
<summary>Parameters</summary>

Parameter   |   Description     | Example
---:        | :---              | :---
id          |   the tag name    |   "kubejs:getting_started"
displayItem |   the icon        |   "minecraft:paper"
title       |   the title       |   "Getting Started"
description |   the description |   "This is a description"
ingredient  |   default item(s) |   ["minecraft:paper", "minecraft:apple", ...]

</details>

<details>
<summary>Example</summary>
<br>

```js
event.createTag("kubejs:getting_started", "minecraft:paper", "Getting started.", "We ponder now!", [    
                    "minecraft:paper",
                    "minecraft:apple",
                    "minecraft:emerald_block",
                ]
);
```

![img](https://github.com/AlmostReliable/ponderjs-forge/wiki/previews/ponder_index.gif)

</details>
</details>
