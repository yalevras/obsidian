
1. Lexical analysis splits up source code into tokens:
```
var average=(min+max)/2;

[var][average][=][(][min][+][max][)][/][2][;]
```
2. Parsing
	This stage is where the parser reports syntax errors.
![[Pasted image 20260209152307.png]]

Lexical analysis and parsing are pretty universal across compilers, after this is when things change based on the compiler.

3. Static analysis is when we analyse our parsed data. For example, a + b, we know to add a and b, but what are a and b? Local or global variables, and where are they defined?

	Statically typed vs. Dynamically typed language
		Type checks are at compile-time vs. at run-time
		Errors are caught by compiler vs. most frequent runtime crashes
		Variable's type is fixed vs. variables can change data type during runtime

	Binding/resolution, is where we wire where an identifier name is and where it is defined together. For statically typed languages, we type check and report a type error if those types don't support being added for example to each other.

	 This semantic insight sometimes get stores back as attributes on the syntax tree, within extra fields in the nodes that aren't initialized during parsing.

	Other times we may store data in a lookup table off to the side, with the keys of the table being identifiers (variable names and declarations). This is called a symbol table.

Everything above is considered the front end of the implementation.

Below is the middle end.

4. Intermediate representations

	The front end is dependent on the source language of the program. The back end is concerned with the final architecture the program will run in. The IR acts as an interface between these two languages.

5. Optimization

	Once we understand what a program means, we can swap it out with something simpler. For example, constant folding. If an expression evaluates to the same value, we can do the evaluation at compile time a replace the code for that expression.

```
pennyArea = 3.14159 * (0.75 / 2) * (0.75 / 2);

becomes

pennyArea = 0.4417860938;
```

Lua and CPython tend to have few compile-time optimiations, and focus most of their performance efforts on the runtime.

Backend starts.

6. Code generation

	Compilers produce virtual machine code, instead of instructions for some real chip. This is bytecode and is binary encoding of the language's low-level operations.

7. Virtual machine

	Instead of translating bytecode to each chip you support (which is not too difficult), you can write a virtual machine, which emulated the chip at runtime.

8. Runtime

	The runtime is a sort of garbage collector to reclaim unused bits, as well as something that can keep track of the type of each object during execution.


**Shortcuts and Alternate Routes**

This is the long way around, and some compilers take a shorter route.

*Single-pass compilers*
Code is outputted straight from the parser without allocating any syntax tree or IRs, meaning the compile needs to know enough about an expression to correctly compile it. This is what C was designed for which is why you can't call a function above the code that defines it unless you have some forward declaration of it, since memory used to be limited.

*Tree-walk interpreters*
Some languages begin executing code right after parsing it to an AST (abstract syntax tree). The interpreter then traverses the syntax tree one branch and leaf at a time, evaluating each node as it goes.

*Transpilers*
Essentially translating your code into another source language to use the existing compilation tools for that language. Used to be called a source-to-source compiler or transcompiler. Nowadays, most languages have a compiler that targets JS, to get your code running in a browser.

*Just-in-time compilation*