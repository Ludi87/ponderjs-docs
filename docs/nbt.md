## Block NBT

```java
modifyTileNBT(Selection selection, Consumer<CompoundTag> consumer, boolean reDrawBlocks)
modifyTileNBT(Selection selection, Consumer<CompoundTag> consumer)
```

Example:

```js
scene.world.modifyTileNBT([2, 3, 3], (nbt) => {
    nbt.Patterns = [
        {
            Color: 0,
            Pattern: "pig"
        }
    ]
})

scene.world.modifyTileNBT([3, 3, 2], (nbt) => {
    nbt.Patterns = [
        {
            Color: 0,
            Pattern: "cre"
        }
    ]
})
```
