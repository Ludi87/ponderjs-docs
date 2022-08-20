# 🏠Structure functions

## Show Structure

```java
scene.showStructure();
```

Shows the whole structure.

* Alternatively, `scene.showBasePlate()` can be used to show the base plate.
* Useful for animating different parts of the structure.

## Show Baseplate

```java
scene.showBasePlate()
```

Show the Baseplate.

## Encapsulate Bounds

```java
scene.encapsulateBounds(blockPos)
```

Encapsulate the structure bounds to given positions.

* This is useful if the custom structure has no proper bounds.
* scene.showStructure() automatically encapsulates the bounds.
