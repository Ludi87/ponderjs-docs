# ⏹ Set/Replace/Modify Blocks

## Set Blocks

```java
setBlock(BlockPos pos, BlockState blockState, boolean spawnParticles)
setBlocks(Selection selection, BlockState blockState)
setBlocks(Selection selection, boolean spawnParticles, BlockState blockState)
```

Examples:

```js
scene.world.setBlocks([0, 1, 0, 4, 1, 4], "minecraft:brick_slab", true)

scene.world.setBlock([0, 1, 1], "minecraft:stone_slab", false)
```

---

## Replace Blocks

```java
replaceBlocks(Selection selection, BlockState state, boolean spawnParticles)
```

Example:

```js
scene.world.replaceBlocks(
    [3, 1, 0, 4, 1, 4],
    "minecraft:oak_slab",
    false)
```

---

## Modify Blocks

```java
modifyBlocks(Selection pos, BlockStateFunction function)
modifyBlocks(Selection selection, boolean spawnParticles, BlockStateFunction function)
modifyBlocks(Selection selection, BlockStateFunction function, boolean spawnParticles)
```

Examples:

```js
scene.world.modifyBlocks(
    [2, 1, 2, 2, 1, 3], 
    (curState) => curState.with("type", "double"), 
    true)

scene.world.modifyBlock(
    [0, 1, 4], 
    (curState) => curState.with("type", "top"), 
    true)

scene.world.modifyBlock(
    [0, 1, 3], 
    () => Block.id("minecraft:jungle_slab").with("type", "top"), 
    true)
```
