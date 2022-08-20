# 📐Sections

## showSection

The first argument is a selection for the section.
To select a specific block, a value can be passed. For areas, an array with two positions is required.
**Remember**: You don't need to use `[x, y, z]` syntax. You can also pass a `vector` or a `blockpos`.

```java
showSection(Selection selection, Direction fadeInDirection)
showSectionAndMerge(Selection selection, Direction fadeInDirection, ElementLink<WorldSectionElement> link)
```

Examples:

```js
scene.world.showSection([x, y, z], Facing.DOWN)

scene.world.showSection([x1, y1, z1, x2, y2, z2], Facing.DOWN)
```

---

## hideSection

```java
hideSection(Selection selection, Direction fadeOutDirection) 
```
