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
Constants and Statics: immutable (unable to be changed) values known at compile time or globally accessible data
use Statements: Import items (functions, types, etc.) from other modules or external crates into the current scope.

We use {} for code blocks. Rust automatically frees associated memory with local variables (according to RAII - Resource Acquisition Is Initialization, which is Rust's resource management). Rust does not require forward declaration of functions or types, you can call a function defined later in the file.

**2.3 The *main* Function: The Entry Point**

```
fn main() {
	println!("Hello, world!");
}
```

*fn main(){
	println!("Hello, world!");
}*
