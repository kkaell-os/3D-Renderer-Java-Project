# \# 3D Renderer

# 

# > \*what if i just made the graphics engine myself\*

# 

# A little experiment where I'm figuring out how 3D rendering actually works by building a renderer in \*\*Java\*\*, basically from the ground up.

# 

# No Unity. No Unreal. No OpenGL doing everything for me.

# 

# Just Java, maths, and \*\*Notepad++\*\*.

# 

# \---

# 

# \## `what is this?`

# 

# I'm making a small software 3D renderer that takes 3D points, transforms them, figures out which pixels belong to each triangle, and draws them onto the screen.

# 

# Right now it's basically a colourful 3D shape floating around in a Swing window.

# 

# The end goal is to understand \*\*why\*\* 3D rendering works, not just how to call a library that does it for me.

# 

# ```text

# &#x20;       3D WORLD

# &#x20;          │

# &#x20;          ▼

# &#x20;     ┌───────────┐

# &#x20;     │  MATRICES │

# &#x20;     └─────┬─────┘

# &#x20;           │

# &#x20;           ▼

# &#x20;     transformed

# &#x20;       vertices

# &#x20;           │

# &#x20;           ▼

# &#x20;     ┌───────────┐

# &#x20;     │ TRIANGLES │

# &#x20;     └─────┬─────┘

# &#x20;           │

# &#x20;           ▼

# &#x20;    rasterization

# &#x20;           │

# &#x20;           ▼

# &#x20;      Z-BUFFER

# &#x20;           │

# &#x20;           ▼

# &#x20;        PIXELS

# ```

# 

# \---

# 

# \## `the tutorial`

# 

# I'm using \*\*\[How to Create Your Own Simple 3D Renderer](http://blog.rogach.org/2015/08/how-to-create-your-own-simple-3d-render.html)\*\* by Rogach as my main guide.

# 

# I'm following the tutorial to learn the concepts and structure, then experimenting with the code myself as I go.

# 

# So yeah, some of this is tutorial-based.

# 

# The point is to eventually reach the stage where I can build and modify this stuff without needing the tutorial open next to me.

# 

# \---

# 

# \## `the setup`

# 

# \*\*Language:\*\* Java

# \*\*Editor:\*\* Notepad++

# \*\*GUI:\*\* Java Swing

# \*\*Renderer:\*\* Software-based

# \*\*IDE:\*\* nope 💀

# 

# I'm deliberately using \*\*Notepad++\*\* for this instead of a full IDE.

# 

# Partly because it's simple.

# 

# Partly because I want to actually understand what's happening instead of having an IDE hold my hand through everything.

# 

# \---

# 

# \## `current stuff\*\*

# 

# \### 3D

# 

# \* `Vertex` objects

# \* `Triangle` objects

# \* X / Y / Z coordinates

# \* 3×3 transformation matrices

# \* Matrix multiplication

# \* Heading rotation

# \* Pitch rotation

# 

# \### Rendering

# 

# \* Triangle rasterization

# \* Barycentric coordinates

# \* Z-buffering

# \* Pixel-by-pixel rendering

# \* `BufferedImage`

# 

# \### Controls

# 

# \* Horizontal rotation slider

# \* Vertical rotation slider

# 

# \---

# 

# \## `what i'm trying to understand`

# 

# The interesting part isn't really the final shape.

# 

# It's everything happening \*\*between this:\*\*

# 

# ```java

# new Vertex(100, 100, 100)

# ```

# 

# and this:

# 

# ```text

# ████████████

# ████████████

# ████████████

# ```

# 

# How do three numbers become a point on a screen?

# 

# How does a computer know which pixels belong inside a triangle?

# 

# How does it know which triangle is in front?

# 

# How do matrices rotate an object in 3D?

# 

# That's what I'm trying to figure out.

# 

# \---

# 

# \## `roadmap`

# 

# ```text

# \[x] Window

# \[x] Vertices

# \[x] Triangles

# \[x] Transformation matrices

# \[x] Heading rotation

# \[x] Pitch rotation

# \[x] Triangle rasterization

# \[x] Barycentric coordinates

# \[x] Z-buffer

# \[ ] Perspective projection

# \[ ] Camera movement

# \[ ] Back-face culling

# \[ ] Lighting

# \[ ] Textures

# \[ ] Load actual 3D models

# \[ ] Probably break everything again

# ```

# 

# \---

# 

# \## `why`

# 

# I'm interested in graphics and programming, but I don't want 3D graphics to just be some mysterious thing that happens inside an engine.

# 

# I want to know what's actually happening.

# 

# So this is me starting at the dumbest possible level:

# 

# \*\*draw the damn triangle myself.\*\*

# 

# \---

# 

# \### made with

# 

# `Java` · `Swing` · `Notepad++` · `math` · `trial \& error` · `probably too much caffeine`



