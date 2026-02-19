If you choose

- Install MSYS2: [https://www.msys2.org](https://www.msys2.org)
    
- Open MSYS2 MinGW64 terminal
    
- Run:
    

`pacman -S mingw-w64-x86_64-gcc`

This gives you:

- gcc
    
- g++
    
- make
    

---

## 2. Install Raylib (for visualization)

In the same MSYS2 MinGW64 terminal:

`pacman -S mingw-w64-x86_64-raylib`

Done. Raylib is now ready.

---

## 3. Install Eigen (math library)

Eigen is header-only.

`pacman -S mingw-w64-x86_64-eigen3`

No compiling required.

---

# Step 2: Project structure

Create folder:

`physics_sim/ ├── main.cpp ├── physics.cpp ├── physics.h`

---

# Step 3: Write physics code

physics.h

`#pragma once  struct Body {     float position;     float velocity;     float acceleration; };  void update(Body& body, float dt);`

---

physics.cpp

`#include "physics.h"  void update(Body& body, float dt) {     body.velocity += body.acceleration * dt;     body.position += body.velocity * dt; }`

This is basic Newtonian integration.

---

# Step 4: Visualization with Raylib

main.cpp

`#include "raylib.h" #include "physics.h"  int main() {      InitWindow(800, 600, "Physics Simulation");      Body body;     body.position = 100;     body.velocity = 0;     body.acceleration = 50;      float dt = 0.016f;      while (!WindowShouldClose()) {          update(body, dt);          BeginDrawing();          ClearBackground(BLACK);          DrawCircle(body.position, 300, 20, RED);          EndDrawing();     }      CloseWindow(); }`

This draws a moving object.

---

# Step 5: Compile

In MSYS2 MinGW64 terminal:

`g++ main.cpp physics.cpp -o sim -lraylib -lopengl32 -lgdi32 -lwinmm`

Run:

`./sim`

You will see a moving circle.

---

# What’s happening conceptually

Your physics simulation runs like this:

`loop:     compute forces     update velocity     update position     draw result`

Visualization is just reading your physics state.

---

# Step 6: Upgrade to real physics simulations

Next things you can add:

**Forces**

`acceleration = force / mass;`

**Gravity**

`acceleration = -9.81;`

**Multiple bodies**

`std::vector<Body> bodies;`

**2D vectors (using Eigen)**

`Eigen::Vector2f position; Eigen::Vector2f velocity;`

---

# Why Raylib is ideal

Raylib is:

- extremely easy
    
- fast
    
- C compatible
    
- used with C and C++
    

Much easier than OpenGL.

---

# What real physics simulators do

They run this loop:

`while (running) {     compute_forces();     integrate_motion();     detect_collisions();     resolve_collisions();     render(); }`

---

# If you want, I can give you a starter template with:

- 2D gravity
    
- multiple bodies
    
- real-time visualization
    
- proper vector math
    

This would be a perfect base for physics experiments.