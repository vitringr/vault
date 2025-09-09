> "Really the best thing you can do at that point is double down on linear algebra, C/C++ and some trigonometry and geometry. Basic physics and optics are helpful too.
>
> Then study shaders and the opengl pipeline, and then study raytracing. That covers like 90% of the job.
>
> Write a game engine once you have it all in your head."

> [!NOTE] Practical Go-Through
> Not everything needs to be completely mastered.
> Feel free to watch videos and read articles without necessarily writing everything down.
> Watch a couple of videos on the same topic, just for clarity.

# Mathematics

_Basics of Linear Algebra and Trigonometry._

Read the book:

- [ ] **Game Math Book**: https://gamemath.com/book/intro.html

- [ ] **3B1B**: The Essence of Linear Algebra (Watch at least 5 videos)

- [ ] **SimonDev**: [What Kind of Math Should Game Developers Know?](https://youtu.be/eRVRioN4GwA)

And then maybe watch the things not so carefully:

- [ ] **Trigonometry Index**: https://www.mathsisfun.com/algebra/trigonometry-index.html

- [ ] https://immersivemath.com/ila/index.html

- [ ] **javidx9**: [Essential Mathematics for Game Developers](https://youtu.be/DPfxjQ6sqrc)

- [ ] **The Player Never Moves**: https://youtu.be/wiYTxjJjfxs

- [ ] **FloatyMonkey Trigonometry**: https://youtu.be/IydbTBZJy7w
- [ ] **FloatyMonkey Vectors**: https://youtu.be/Ej3ZVxljJfo
- [ ] **FloatyMonkey Matrices and Transformations**: https://youtu.be/HgQzOmnBGCo

# Graphics Concepts

- [ ] **Perspective Projection**: https://youtu.be/U0_ONQQ5ZNM

- [ ] **Homogeneous Coordinates**: https://youtu.be/o-xwmTODTUI

# Software Rasterizer

_Build a software rasterizer from scratch._

- [ ] **Daniel Shiffman**: [3D Rendering with Rotation and Projection](https://youtu.be/p4Iz0XJY-Qk)

- [ ] **Tiny Renderer**: https://haqr.eu/tinyrenderer/
- [ ] **Tiny RayTracing**: https://github.com/ssloy/tinyraytracer/wiki/Part-1:-understandable-raytracing

- [ ] **Tscoding**: [C pixel-by-pixel Software 3D rendering](https://youtu.be/xdShzvCZPBk)

- [ ] **Graphics Engine from Scratch (short, JS)**: https://youtu.be/ZnycovL2qWU

- [ ] **Sebastian Software Rasterizer**: https://youtu.be/yyJ-hdISgnw

# OpenGL

_Learn OpenGL and Shaders, and probably stop there._

- [ ] https://learnopengl.com/

> "Your main goal at this stage is to understand how GPU rendering works, implement classic algorithms like shadow mapping and deferred rendering, and create your own physically based renderer. We believe that these are the topics which any graphic engineer should understand to be ready for real job in rendering team."

> "Note that even with OpenGL you can write almost everything, including 2D renderer, first-person shooter game or general-purpose game engine. It is okay spending a year on a project which seemed simple at first glance, as long as it helps you to learn and give you a joy."

# Technology

Research and choose a technology to use.

Raylib: https://youtu.be/UoAsDlUwjy0

Current List: Raylib > Godot > SDL3 > Bevy > C

The absolute requirements of the technology are:

- open source license
- cross-platform builds
- good performance

_The need is to know and understand, not to implement and reinvent._

Right now, Raylib wins.

# Dimensions

The choice between 2D, 2.5D, and 3D.

All have their pros and cons.

Mostly dependent on the artist, if any.

**Simulation**: The type of graphics should not be of early concern, as the simulation of game mechanics should be separated from the game view, meaning that the same reusable components of mechanics should work with any graphics.

- Can build an advanced simulation way before any graphics.

# GAME DEVELOPMENT

Build modular & reusable components for the type of game.

For example, if it's HnS, build stuff like character controller, health, healthbars, AI, UI, stats, attacks...

Having reusable components will make designing and prototyping ideas much easier.

_**THE DREAM**_
