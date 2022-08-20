# Misc

## Idle

```java
scene.idle(ticks);
scene.idleSeconds(seconds)
```

`idle(ticks)` or `idleSeconds(seconds)` is used to wait for a certain amount of time.

```java
scene.world.createEntity(EntityType<?> entityType, Vec3 position, Consumer<EntityJS> consumer)
```

## Create Entity

* `.createEntity()` returns an entity link from Create which will be used as reference in the future
* `[x, y, z]` is the position but any KubeJS way to represent a position can be used.

## Display Text

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

## Show Controls

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
