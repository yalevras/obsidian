**3.1 Point operators**
Where each output pixel's value depends on only the corresponding input pixel value. Examples include brightness, contrast, colour correction, and transformations.

**3.1.1 Pixel transforms**
Takes in input image, produces output image. In cont. domain, this is denoted as:
$$g(x)=h(f(x))\quad or\quad g(x)=h(f_0),...,f_n(x)),$$
*x* = D-dimensional (D = 2 for image) *domain* of the input and output functions *f* and *g*
These operate over a scalar or vector range. For discrete (sampled images), the domain consists of *pixel locations*, *x = (i, j)*
$$g(i,j)=h(f(i,j)),$$
A common point process is adding a constant *a > 0* for multiplication (*gain*) and* *b* for addition 
(*bias*) often controlling *contrast* and *brightness* 
$$g(x)=a(x)f(x)+b(x)$$
[[Superposition]] 
