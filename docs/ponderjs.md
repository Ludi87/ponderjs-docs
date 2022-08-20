# PonderJS Docs

## Getting Started

Before we start, make sure [KubeJS](https://www.curseforge.com/minecraft/mc-mods/kubejs) and [Create](https://www.curseforge.com/minecraft/mc-mods/create) are installed.
All PonderJS scripts will be located inside the `client_scripts` folder. If you don't know where to find it, please take a look at the [KubeJS wiki](https://kubejs.com/).

## Type Syntax

In PonderJS some functions will need a selection, block position or a vector. The selection is an area between two positions or vectors.

KubeJS and PonderJS provide a simple syntax to pass a position or vector to a function.

Passing an array with three values `[x, y, z]` to a function that requires a selection, block position or vector will automatically wrap the array to the corresponding type.

If you want to shorthand a selection area you can pass in the following types:

* [x1, y1, z1, x2, y2, z2]
* [vector1, vector2]
* [blockPos1, blockPos2]
* [[x, y, z], [x, y, z]]
If you dislike the shorthand syntax, you can always use the functions provided in the `util` object in your Ponder scenes. You can read more about it here.
