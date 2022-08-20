# 🔀Misc

## Idle

`idle(ticks)` or `idleSeconds(seconds)` is used to wait for a certain amount of time.

```java
scene.idle(ticks);
scene.idleSeconds(seconds)
```

## Create Entity

`.createEntity()` returns an entity link from Create which will be used as reference in the future.
`[x, y, z]` is the position, but any KubeJS way to represent a position can be used.

```java
scene.world.createEntity(EntityType<?> entityType, Vec3 position, Consumer<EntityJS> consumer)
```

---

## Display Text

```java
scene.text(int duration, String text)
scene.text(int duration, String text, Vec3 position)
scene.text(int duration, ResourceLocation key)
```

| Optional:   | <!-- -->    |
|-------------|-------------|
| `.colored(Ponderpalette color)` | Sets the color of the text.
| `.placeNearTarget()`            | Places  the text closer to the target position.
| `.attachKeyFrame()`             | Adds a keyframe to the scene.

Example:

```js
scene.text(60, "Example text", [2.0, 2.5, 2.5])
    .colored(PonderPalette.RED)
    .placeNearTarget()
    .attachKeyFrame()
```

---

## Show Controls

```java
scene.showControls(int duration, Vec3 pos, Pointing pointing)
```

| method            | description   |
|-------------------|---|
 `.rightClick()`   | Uses mouse right click as icon.
 `.leftClick()`    | Alternatively, `.leftClick()` can be used
 `.showing(icon)`  | or `.showing(icon)` for a custom icon.
 `.withItem(item)` | Defines the item that should be shown with the icon.
 `.whileSneaking()`| **Optional** Defines that controls are only shown when sneaking.
 `.whileCTRL()`    | **Optional** Defines that controls are only shown when holding CTRL.
`.whileSneaking()` and `withCTRL()` can not be used simultaneously.

Example:

```js
scene.showControls(60, [2.5, 3, 2.5], "down")
    .rightClick()
    .withItem("shears")
    .whileSneaking()
```

---

## PonderPalette

Possible values:

```js
⚪ PonderPalette.WHITE
⚫ PonderPalette.BLACK
🔴 PonderPalette.RED
🟢 PonderPalette.GREEN
🔵 PonderPalette.BLUE
```

* PonderPalette.SLOW
* PonderPalette.MEDIUM
* PonderPalette.FAST

* PonderPalette.INPUT
* PonderPalette.OUTPUT
