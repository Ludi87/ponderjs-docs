# 🔧Utils

## Grid

Creates a new BlockPos at `x, y, z`.

```js
util.grid.at(x, y, z)
```

Creates a new BlockPos at 0, 0, 0.

```js
util.grid.zero()
```

## Vector

Creates a new Vector at `x, y, z` or at the `blockpos`.

```js
util.vector.centerOf(x, y, z)
util.vector.centerOf(blockPos)
```

Creates a new vector on top of `x, y, z` or the `blockpos`.

```js
util.vector.topOf(x, y, z)
util.vector.topOf(blockPos)
```

Creates a new vector at the specified surface direction.

```js
util.vector.blockSurface(blockPos, direction)
util.vector.blockSurface(blockPos, direction, margin)
```

## Selection

Creates a selection of the **whole structure**.

```js
util.select.everywhere()
```

Creates a selection at the given **position**.

```js
util.select.position(x, y, z)
util.select.position(blockPos)
```

Creates a selection for the given **area**.

```js
util.select.fromTo(x1, y1, z1, x2, y2, z2)
util.select.fromTo(blockPos1, blockPos2)
```

Creates a selection for the given **x** and **y**.

```js
util.select.column(x, y)
```

Creates a selection for a **layer at y**.

```js
util.select.layer(y)
util.select.layers(y, height)
```

Creates a selection from a **blockPos** with given **size** as vector.

```js
util.select.cubdoid(blockPos, vector)
```
