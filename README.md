# 🧊 3D Renderer

### *what if i just made the graphics engine myself?*

![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Swing](https://img.shields.io/badge/GUI-Swing-blue?style=for-the-badge)
![Software Rendered](https://img.shields.io/badge/Rendering-100%25_Software-critical?style=for-the-badge)
![Notepad++](https://img.shields.io/badge/Editor-Notepad++-90E59A?style=for-the-badge&logo=notepadplusplus&logoColor=black)
![IDE](https://img.shields.io/badge/IDE-nope_💀-lightgrey?style=for-the-badge)

**No Unity. No Unreal. No OpenGL doing the hard part for me.**
Just Java, maths, and a text editor.

---

## 📖 What is this?

A small **software 3D renderer** built from the ground up in Java. It takes 3D points, transforms them with matrices, works out which pixels belong to each triangle, and paints them onto a Swing window, one pixel at a time.

<img width="477" height="485" alt="image" src="https://github.com/user-attachments/assets/9244f99d-f31a-4693-ae31-d35f5c6a7620" />
<img width="475" height="485" alt="image" src="https://github.com/user-attachments/assets/5639072f-d3a5-4a09-8921-11c2909dcd6e" />
<img width="479" height="481" alt="image" src="https://github.com/user-attachments/assets/f51a7a23-04b3-42ee-8a66-1c1b9c2c662f" />



Right now it's a colourful 3D shape floating around in a window, and you can spin it with sliders.

The end goal isn't a pretty shape. It's understanding **why** 3D rendering works, not just which library call makes it happen.

```text
        3D WORLD
           │
           ▼
     ┌───────────┐
     │  MATRICES │   rotate / transform every vertex
     └─────┬─────┘
           │
           ▼
      transformed
       vertices
           │
           ▼
     ┌───────────┐
     │ TRIANGLES │   3 vertices = 1 face
     └─────┬─────┘
           │
           ▼
     rasterization    "which pixels are inside?"
           │
           ▼
       Z-BUFFER       "which triangle is in front?"
           │
           ▼
        PIXELS        BufferedImage → screen
```

---

## 🎓 The tutorial

I'm following **[How to Create Your Own Simple 3D Renderer](http://blog.rogach.org/2015/08/how-to-create-your-own-simple-3d-render.html)** by Rogach as my main guide.

I'm using it to learn the concepts and structure, then experimenting with the code myself as I go. So yes, parts of this are tutorial-based. The point is to reach the stage where I can build and modify all of it **without** the tutorial open next to me.

---

## 🛠️ The setup

| | |
|---|---|
| **Language** | Java |
| **GUI** | Java Swing |
| **Renderer** | Pure software (CPU only) |
| **Editor** | Notepad++ |
| **IDE** | nope 💀 |

I'm deliberately avoiding a full IDE. It's simpler, and I want to understand what's happening instead of having something hold my hand through every step.

---

## ✨ What it does right now

### 🔷 3D maths
- `Vertex` and `Triangle` objects
- X / Y / Z coordinates
- 3×3 transformation matrices
- Matrix multiplication
- Heading (horizontal) rotation
- Pitch (vertical) rotation

### 🎨 Rendering
- Triangle rasterization
- Barycentric coordinates
- Z-buffering
- Pixel-by-pixel drawing into a `BufferedImage`

### 🎮 Controls
- Horizontal rotation slider
- Vertical rotation slider

---

## 🧠 What I'm trying to understand

The interesting part isn't the final shape. It's everything that happens **between this:**

```java
new Vertex(100, 100, 100)
```

**and this:**

```text
████████████
████████████
████████████
```

The questions driving the whole project:

- 🔹 How do three numbers become a point on a screen?
- 🔹 How does the computer know which pixels are *inside* a triangle?
- 🔹 How does it know which triangle is *in front*?
- 🔹 How do matrices rotate an object in 3D?

### Quick cheat sheet (my notes so far)

**Rotation is just matrix multiplication.** Heading spins around the Y axis, pitch around the X axis:

```text
Heading (Y axis)            Pitch (X axis)
┌                 ┐         ┌                 ┐
│  cos θ   0  −sin θ │      │  1     0      0    │
│    0     1    0    │      │  0   cos φ  sin φ  │
│  sin θ   0   cos θ │      │  0  −sin φ  cos φ  │
└                 ┘         └                 ┘
```

**Barycentric coordinates** describe any point as a weighted mix of a triangle's three corners. If all three weights are ≥ 0, the pixel is inside the triangle.

**Z-buffer** keeps the closest depth seen so far for every pixel. A new pixel only gets drawn if it's closer than what's already there.

---

## 🚀 Running it

Grab the source, then from the project folder:

```bash
javac *.java
java Main
```

> Swap `Main` for whichever class holds your `main` method. You just need a JDK installed.

---

## 🗺️ Roadmap

```text
[x] Window
[x] Vertices
[x] Triangles
[x] Transformation matrices
[x] Heading rotation
[x] Pitch rotation
[x] Triangle rasterization
[x] Barycentric coordinates
[x] Z-buffer
[ ] Perspective projection
[ ] Camera movement
[ ] Back-face culling
[ ] Lighting
[ ] Textures
[ ] Load actual 3D models
[ ] Probably break everything again
```

---

## 💭 Why?

I'm into graphics and programming, but I don't want 3D to be a mysterious thing that just happens inside an engine. I want to know what's actually going on.

So this is me starting at the dumbest possible level:

> **draw the damn triangle myself.**

---

### made with

`Java` · `Swing` · `Notepad++` · `math` · `trial & error` · `probably too much caffeine` ☕
