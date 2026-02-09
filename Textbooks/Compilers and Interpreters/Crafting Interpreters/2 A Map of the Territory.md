
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
		