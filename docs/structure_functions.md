# 🏠Structure functions

## Show Structure

Shows the whole structure.

* Alternatively, `scene.showBasePlate()` can be used to show the base plate.
* Useful for animating different parts of the structure.

```java
scene.showStructure();
```

---

## Show Baseplate

Show the Baseplate.

```java
scene.showBasePlate()
```

---

## Encapsulate Bounds

Encapsulate the structure bounds to given positions.

* This is useful if the custom structure has no proper bounds.
* scene.showStructure() automatically encapsulates the bounds.

```java
scene.encapsulateBounds(blockPos)
```
