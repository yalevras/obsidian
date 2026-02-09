**2.1 Compiling**
Rust compiler: rustc, centered around Cargo, a build system which acts as a frontend for compiling code and managing external libraries called **crates**. It combines the roles of make, cmake, and apt.
```
cargo new my_project
cd my_project

cargo build

cargo run
```

**2.2 Basic Program Structure**

Modules: logical units of code (public/private)
Functions: same old
Type Defs: custom data structures using struct, enum, or type aliases (type)
Constants and Statics: immutable values