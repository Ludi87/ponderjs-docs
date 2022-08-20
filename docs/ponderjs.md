# Ponder

## Structure functions

#### Show Baseplate

```java
scene.showBasePlate()
```

Show the Baseplate.

#### Encapsulate Bounds

```java
scene.encapsulateBounds(blockPos)
```

Encapsulate the structure bounds to given positions.

* This is useful if the custom structure has no proper bounds.
* scene.showStructure() automatically encapsulates the bounds.

#### Show Structure

```java
scene.showStructure();
```

Shows the whole structure.

* Alternatively, `scene.showBasePlate()` can be used to show the base plate.
* Useful for animating different parts of the structure.

## Misc

#### Idle

```java
scene.idle(ticks);
scene.idleSeconds(seconds)
```

`idle(ticks)` or `idleSeconds(seconds)` is used to wait for a certain amount of time.


```java
scene.world.createEntity(EntityType<?> entityType, Vec3 position, Consumer<EntityJS> consumer)
```

#### Create Entity

* `.createEntity()` returns an entity link from Create which will be used as reference in the future
* [x, y, z] is the position but any KubeJS way to represent a position can be used.

#### Display Text

```java
scene.text(int duration, String text)
scene.text(int duration, String text, Vec3 position)
scene.text(int duration, ResourceLocation key)
```

Optional:

```java
.colored(Ponderpalette color) // Sets the color of the text.
.placeNearTarget()            // Places the text closer to the target position.
.attachKeyFrame()             // Adds a keyframe to the scene.
```

Example:

```js
scene.text(60, "Example text", [2.0, 2.5, 2.5])
    .colored(PonderPalette.RED)
    .placeNearTarget()
    .attachKeyFrame()
```

#### Show Controls

```java
scene.showControls(int duration, Vec3 pos, Pointing pointing)
```

```java
.leftClick()
.rightClick()
.showing(icon)
.withItem("shears")
.whileSneaking()
.whileCTRL()
```

Example:

```js
scene.showControls(60, [2.5, 3, 2.5], "down")
    .rightClick()
    .withItem("shears")
    .whileSneaking()
```

## Set/Replace/Modify Blocks

#### Set Blocks

```java
setBlock(BlockPos pos, BlockState blockState, boolean spawnParticles)
setBlocks(Selection selection, BlockState blockState)
setBlocks(Selection selection, boolean spawnParticles, BlockState blockState)
```

* First method sets blocks with default particle spawning

Examples:

```js
scene.world.setBlocks(
    [0, 1, 0, 4, 1, 4], 
    "minecraft:brick_slab", 
    true);
```

```js
scene.world.setBlock(
    [0, 1, 1], 
    "minecraft:stone_slab", 
    false);
```

#### Replace Blocks

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

#### Modify Blocks

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
```

```js
scene.world.modifyBlock(
    [0, 1, 4], 
    (curState) => curState.with("type", "top"),
    true)
```

```js
scene.world.modifyBlock(
    [0, 1, 3], 
    () => Block.id("minecraft:jungle_slab").with("type", "top"), 
    true)
```

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

## Sections

#### showSection

```java
showSection(Selection selection, Direction fadeInDirection)
showSectionAndMerge(Selection selection, Direction fadeInDirection, ElementLink<WorldSectionElement> link)
```

* The first argument is a selection for the section.
* To select a specific block, a value can be passed. For areas, an array with two positions is required.

* **Remember**: You don't need to use `[x, y, z]` syntax. You can also pass a `vector` or a `blockpos`.

Example:

```js
scene.world.showSection([x, y, z], Facing.DOWN)
scene.world.showSection([x1, y1, z1, x2, y2, z2], Facing.DOWN)
```

#### hideSection

```java
hideSection(Selection selection, Direction fadeOutDirection) 
```

## Utils

#### Grid

Creates a new BlockPos at `x, y, z`.

```js
util.grid.at(x, y, z)
```

Creates a new BlockPos at 0, 0, 0.
```js
util.grid.zero()
```

#### Vector

Creates a new Vector at x, y, z or at the blockpos.

```js
util.vector.centerOf(x, y, z)
util.vector.centerOf(blockPos)
```

Creates a new vector on top of x, y, z or the blockpos.

```js
util.vector.topOf(x, y, z)
util.vector.topOf(blockPos)
```

Creates a new vector at the specified surface direction.

```js
util.vector.blockSurface(blockPos, direction)
util.vector.blockSurface(blockPos, direction, margin)
```

#### Selection

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

## Particles

### Constants for examples

```js
const TICK_LENGTH = 20
const IDLE_TICK_LENGTH = TICK_LENGTH * 3
const pos = [4, 1.5, 4]
const start = [0, 1, 0]
const end = [2, 2, 3]
```

#### Simple

```java
simple(int ticks, ParticleType<?> type, Vec3 pos)
```

Examples:

```js
scene.particles.simple(TICK_LENGTH, "glow", pos);
scene.particles.simple(TICK_LENGTH, "glow", start)
    .density(10)
    .area(end)

scene.particles.simple(TICK_LENGTH, "small_flame", pos);
scene.particles.simple(TICK_LENGTH, "small_flame", start)
    .density(10)
    .motion([0, 0, -0.1])
    .area(end)

scene.particles.simple(TICK_LENGTH, "portal", start)
    .density(6)
    .withinBlockSpace()
```

Examples with custom transformations:

```js
scene.particles.simple(TICK_LENGTH * 3, "glow", [1, 1.5, 0])
    .transformPosition((tick, p) => {
        return [p.x(), p.y(), p.z() + (tick / TICK_LENGTH) * 1.6]
    }
);

scene.particles.simple(TICK_LENGTH * 3, "sneeze", [2.5, 1.5, 0])
    .transformMotion((tick, m) => {
        return [0, 0, (tick / TICK_LENGTH) * 0.2]
    }
);

scene.particles.simple(TICK_LENGTH * 3, "small_flame", [4, 1.5, 0])
    .transform((tick, p, m) => {
        return [
            [p.x(), p.y(), Math.random() * 5],
            [(tick / TICK_LENGTH) * 0.2, 
            0, 
            (tick / TICK_LENGTH) * 0.2],
        ]
    }
)
```

#### Item

```java
item(int ticks, ItemStack item, Vec3 pos)
```

Examples:

```js
scene.particles.item(TICK_LENGTH, "minecraft:diamond_block", pos)
    .motion([-0.09, 0.3, 0])
    .density(8)
scene.particles.item(TICK_LENGTH, "minecraft:diamond_block", start)
    .area(end)
```

#### Block

```java
block(int ticks, BlockState blockState, Vec3 pos)
```

Examples:

```js
scene.particles.block(TICK_LENGTH, "minecraft:diamond_block", pos);
scene.particles.block(TICK_LENGTH, "minecraft:diamond_block", start)
    .density(4)
    .area(end)
```

#### Dust

```java
dust(int ticks, Color color, Vec3 pos)
dust(int ticks, Color fromColor, Color toColor, Vec3 pos)
```

Examples:

```js
scene.particles.dust(TICK_LENGTH, "#00FFF0", start)
    .density(5)
    .motion([0, 0, -0.1])
    .area(end)
    .roll(10)

scene.particles.dust(TICK_LENGTH, "#FF0000", "#0000FF", start)
    .density(2)
    .scale(2.1)
    .motion([0, 0, -0.1])
    .area(end)
    .roll(3)
```

### Constants for following examples

```js
const delta = [0.3, 0.3, 0.3]
const fluidPos = new Vec3(0.5, 1.5, 0.5)
const potionFluid = Fluid.of("create:potion", { Potion: "minecraft:blindness" });
```

#### Fluid

```java
fluid(int ticks, FluidStackJS fluid, Vec3 pos)
```

Examples:

```js
scene.particles.fluid(TICK_LENGTH, "lava", fluidPos.add([0, 0, 0]))
    .delta(delta)
    .density(5)

scene.particles.fluid(TICK_LENGTH, "create:honey", fluidPos.add([0, 0, 2]))
    .delta(delta)
    .density(5)

scene.particles.fluid(TICK_LENGTH, potionFluid, fluidPos.add([0, 0, 4]))
    .delta(delta)
    .collision(true)
    .density(5)
```

#### Drip

```java
drip(int ticks, FluidStackJS fluid, Vec3 pos) 
```

Examples:

```js
scene.particles.drip(TICK_LENGTH, "lava", fluidPos.add([2, 0, 0]))
    .delta(delta)
    .density(5)

scene.particles.drip(TICK_LENGTH, potionFluid, fluidPos.add([2, 0, 4]))
    .delta(delta)
    .collision(true)
    .density(5);    
```

#### Basin

```java
basin(int ticks, FluidStackJS fluid, Vec3 pos) 
```

Examples:

```js
scene.particles.basin(TICK_LENGTH, "lava", fluidPos.add([4, 0, 0]))
    .delta(delta)
    .density(5)

scene.particles.basin(TICK_LENGTH, "create:honey", fluidPos.add([4, 0, 2]))
    .delta(delta)
    .density(5)

scene.particles.basin(TICK_LENGTH, potionFluid, fluidPos.add([4, 0, 4]))
    .delta(delta)
    .collision(true)
    .density(5)
```

#### RotationIndicator

```java
rotationIndicator(int ticks, Vec3 pos, float radius1, float radius2, Direction.Axis axis)
```

Example:

```js
scene.particles.rotationIndicator(TICK_LENGTH, [2.5, 1.5, 2.5], 1, 0.5, "Z")
    .rotationSpeed(4)
    .color("#FF0000");
```

* The 1 is the first radius, the 0.5 is the second radius.
* The last argument is the axis "X", "Y" or "Z".
