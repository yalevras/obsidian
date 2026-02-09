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
*println!* prints a new line at the end
*print!* does not

to print variables

```
let local_variable = "argument";
println!("this is an {local_variable}!");
```

Rust's main function returns the unit type (), indicating success, this can be changed later.

**2.4 Variables: Immutability by Default**
```
let variable_name: OptionalType = value;
```
Variables must be initialized before their first usage. Variables are immutable by default.

Example:
```
fn main() {
	let x: i32 = 5;
	// x = 6; // This line would cause a compile-time error!
	println!("The value of x is: {}", x);
}
```

To enable mutability, we can use the mut keyword.
```
fn main() {
	let mut x = 5;
	println("The initial value of x is: {}", x);
	x = 6;
	println!("The new value of x is: {}", x);
}
```

In Rust, variables are automatically like const in C.