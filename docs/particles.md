# 🌟Particles

**Constants for following examples:**

```js
const TICK_LENGTH = 20
const IDLE_TICK_LENGTH = TICK_LENGTH * 3
const pos = [4, 1.5, 4]
const start = [0, 1, 0]
const end = [2, 2, 3]
const delta = [0.3, 0.3, 0.3]
const fluidPos = new Vec3(0.5, 1.5, 0.5)
const potionFluid = Fluid.of("create:potion", { Potion: "minecraft:blindness" });
```

## Simple

```java
simple(int ticks, ParticleType<?> type, Vec3 pos)
```

<details>
<summary>Examples:</summary>

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

</details>

---

## Item

```java
item(int ticks, ItemStack item, Vec3 pos)
```

<details>
<summary>Examples:</summary>

```js
scene.particles.item(TICK_LENGTH, "minecraft:diamond_block", pos)
    .motion([-0.09, 0.3, 0])
    .density(8)

scene.particles.item(TICK_LENGTH, "minecraft:diamond_block", start)
    .area(end)
```

</details>

---

## Block

```java
block(int ticks, BlockState blockState, Vec3 pos)
```

<details>
<summary>Examples:</summary>

```js
scene.particles.block(TICK_LENGTH, "minecraft:diamond_block", pos);

scene.particles.block(TICK_LENGTH, "minecraft:diamond_block", start)
    .density(4)
    .area(end)
```

</details>

---

## Dust

```java
dust(int ticks, Color color, Vec3 pos)
dust(int ticks, Color fromColor, Color toColor, Vec3 pos)
```

<details>
<summary>Examples:</summary>

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

</details>

---

## Fluid

```java
fluid(int ticks, FluidStackJS fluid, Vec3 pos)
```

<details>
<summary>Examples:</summary>

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

</details>

---

## Drip

```java
drip(int ticks, FluidStackJS fluid, Vec3 pos) 
```

<details>
<summary>Examples:</summary>

```js
scene.particles.drip(TICK_LENGTH, "lava", fluidPos.add([2, 0, 0]))
    .delta(delta)
    .density(5)

scene.particles.drip(TICK_LENGTH, potionFluid, fluidPos.add([2, 0, 4]))
    .delta(delta)
    .collision(true)
    .density(5);    
```

</details>

---

## Basin

```java
basin(int ticks, FluidStackJS fluid, Vec3 pos) 
```

<details>
<summary>Examples:</summary>

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

</details>

---

## RotationIndicator

```java
rotationIndicator(int ticks, Vec3 pos, float radius1, float radius2, Direction.Axis axis)
```

<details>
<summary>Example:</summary>

* The 1 is the first radius, the 0.5 is the second radius.
* The last argument is the axis "X", "Y" or "Z".

```js
scene.particles.rotationIndicator(TICK_LENGTH, [2.5, 1.5, 2.5], 1, 0.5, "Z")
    .rotationSpeed(4)
    .color("#FF0000");
```

</details>
