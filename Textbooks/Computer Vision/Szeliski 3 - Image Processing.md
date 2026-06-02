**3.1 Point operators**
Where each output pixel's value depends on only the corresponding input pixel value. Examples include brightness, contrast, colour correction, and transformations.

**3.1.1 Pixel transforms**
![[Pasted image 20260206161649.png]]
a) Original, b) b = 16, c) a = 1.1 d) γ = 1.2
Takes in input image, produces output image. In cont. domain, this is denoted as:
$$g(x)=h(f(x))\quad or\quad g(x)=h(f_0),...,f_n(x)),$$
*x* = D-dimensional (D = 2 for image) *domain* of the input and output functions *f* and *g*
These operate over a scalar or vector range. For discrete (sampled images), the domain consists of *pixel locations*, *x = (i, j)*
$$g(i,j)=h(f(i,j)),$$
A common point process is adding a constant *a > 0* for multiplication (*gain*, obeys the *[[Superposition]]* principle ) and *b* for addition (*bias*) often controlling *contrast* and *brightness* 
$$g(x)=a(x)f(x)+b(x)$$
These constants get applied to each RGB value of each pixel.

Another *dyadic* (two-input) operator is the *linear blend* operator is below. By varying *a* from 
*0 -> 1* we can perform a temporal cross-dissolve between two images or videos, or as a component of image morphing algorithms.

$$g(x)=(1-a)f_0(x)+af_1(x)$$

![[Pasted image 20260206161232.png|350]]

Gamma correction is a non-linear transform, removing the non-linear mapping between input radiance and quantized pixel values. To invert the gamma (γ = 2.2 usually) mapping applied by the sensor we use
$$g(x)=[f(x)]^{1/γ}$$