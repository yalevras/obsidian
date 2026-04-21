https://pomodo.io/tech-archive/jpeg-definitive-guide/

JPEG - Joint Photographic Experts Group

Lossy compression - some data is lost when saved

![[Pasted image 20260421114613.png]]

Progressive JPEGs also exist and they load faster in progressive waves.

JPEG is the compression specification, the file format is a JPEG File Interchange Format (JFIF). This wrapper holds the data created by JPEG compression. EXIF is used more commonly for photography, but also uses the .jpeg extension, it just includes information about the photo in its metadata.

Outside of the JPEG spec,
JFIF defines: component sample registration, resolution and aspect ratio, and color space.
EXIF defines: camera settings (make, model, orientation (rotation), aperture, shutter speed, focal length, metering mode, and ISO speed information), image metrics (pixel dimensions, resolution, colorspace, and file size), date and time, location, thumbnail, description, copyright information.

![JFIF file holds JPEG Compressed Data.](https://res.cloudinary.com/thewebmaster/image/upload/images/blog/jpeg-images-definitive-guide/jpeg-encoding.svg)
**color Transformation**
A colorspace represents a specific organization of colors that can be represented by a color model.
A color model is a mathematical formula used to calculate those colors, such as RGB and CMYK.
![RBG and CMYK Colorspace Example.](https://res.cloudinary.com/thewebmaster/image/upload/images/blog/jpeg-images-definitive-guide/rgb-cmyk-colorspace-example.svg)
![RBG and CMYK Colorspace Example.](https://res.cloudinary.com/thewebmaster/image/upload/images/blog/jpeg-images-definitive-guide/rgb-cmyk-example.svg)
You can convert color models to another very easily, JPEG converts RGB to the YCbCr color model
![Contrast sensitivity of the eye.|300](https://res.cloudinary.com/thewebmaster/image/upload/images/blog/jpeg-images-definitive-guide/contrast_sensitivity_of_the_eye.svg)


This subtraction can be mathematically extracted instead of encoded.

**Chroma Subsampling**
Where the color information in an image's Cb and Cr channels is sampled at a lower resolution than the original. Common subsampling ratios for JPEGs:
- 4:4:4 - no sub sampling
- 4:2:2 - reduction by half in the horizontal direction (50% area reduction)
- 4:2:0 - reduction by half in both the horizontal and vertical directions (75% area reduction)
- 4:1:1 - reduction by a quarter in the horizontal direction (75% area reduction)
J:a:b, where J is the horizontal sampling reference, usually four pixels, a is the number of chrominance samples (Cr, Cb) in the first row of J pixels, and b is the change between the first and second row of chrominance pixels, either 0 or a
![JPEG subsampling ratios.](https://res.cloudinary.com/thewebmaster/image/upload/images/blog/jpeg-images-definitive-guide/chroma-subsampling-ratio-examples.svg)
![[Pasted image 20260421135741.png]]
This downsampling is lossy, but provides file size savings. Adding JPEG compression and the size reduces much more.
![[Pasted image 20260421140605.png]]
![[Pasted image 20260421140853.png]]
**Chroma Subsampling Artifacts**
These are most visible where there is a bold transition between colors
![Resampling artifacts.](https://res.cloudinary.com/thewebmaster/image/upload/images/blog/jpeg-images-definitive-guide/image-artifacts-resampling.svg)
![Resampling artifacts.](https://res.cloudinary.com/thewebmaster/image/upload/images/blog/jpeg-images-definitive-guide/chroma-subsampling-image-artifacts.svg)
Chroma subsampling should be avoided where there are abrupt color changes, ad when using colored text or text on colored backgrounds which can make text very dull.
![[Pasted image 20260421142322.png]]
![[Pasted image 20260421142442.png]]

**JPEG Encoding: Block Splitting**
Process of splitting each channel in a source image into pixel blocks called Minimum Coded Units (MCU). These MCUs can be different-sized depending on whether that channel was subsampled.

MCU size for subsampling ratios:
- 4:4:4 - 8x8 pixels
- 4:2:2 - 16x8 pixels
- 4:2:0 - 16x16 pixels

Image dimensions must be multiples of an MCU. If not, we can extend the image to make the correct size. The JPEG encoding process is then gone through and the additional pixels are removed.
![[Pasted image 20260421160516.png]]

**Blocking Artifacts**
Division into MCUs may cause visual discontinuities if compressed at very low quality.
![[Pasted image 20260421162443.png]]

**JPEG Encoding: Discrete Cosine Transform (DCT)**
Each 8x8 MCU for each channel (Y, Cb, Cr) is converted from a spatial domain representation to a frequency domain representation using a two-dimensional type-II discrete cosine transform.

We apply a series of DCTs:
![JPEG standard Cosine Values.](https://res.cloudinary.com/thewebmaster/image/upload/images/blog/jpeg-images-definitive-guide/consine-transforms-jpeg.svg)
We first convert to a frequency-domain representation by assigning a number to each pixel in a matrix, falling between 0 and 255 where darker pixels are lower and lighter pixels are higher.
![JPEG Frequency-domain Representation.](https://res.cloudinary.com/thewebmaster/image/upload/images/blog/jpeg-images-definitive-guide/frequency-domain-representation.svg)
Subtract 128 from each number to center around 0.
![Discrete Cosine Transform Recenter on Zero.](https://res.cloudinary.com/thewebmaster/image/upload/images/blog/jpeg-images-definitive-guide/DCT-recenter-on-zero.svg)
Calculate the 2D DCT coefficients using
![Discrete Cosine Transform Formula.](https://res.cloudinary.com/thewebmaster/image/upload/images/blog/jpeg-images-definitive-guide/discrete-cosine-transform-formula.svg)
Resulting in this
![Discrete Cosine Transform Recenter on Zero.](https://res.cloudinary.com/thewebmaster/image/upload/images/blog/jpeg-images-definitive-guide/calculate-DCT.svg)
There are two types of DCT coefficients:
- DC coefficient - the top left-hand corner DCT coefficient, aka the constant component, defining the basic hue for the entire block
- AC coefficients - the remaining 63 DCT coefficients, otherwise known as the alternating components

These values are then divided by quantization matrices for Luminance and Chrominance channels depending on quality (only for Luminance)

![Luminance Quantization Matrix - 50% quality.](https://res.cloudinary.com/thewebmaster/image/upload/images/blog/jpeg-images-definitive-guide/quantization-matrix-50-percent-quality.svg)
![Chroma Quantization Matrix - 50% quality.](https://res.cloudinary.com/thewebmaster/image/upload/images/blog/jpeg-images-definitive-guide/quantization-matrix-chroma-channels.svg)

To then quantize the DCT coefficients:
![[Pasted image 20260421170243.png]]
B = the quantized DCT coefficient
G = the DCT coefficient
Q = the quantization matrix
![[Pasted image 20260421170327.png]]
Result:
![Quantized DCT Coefficients.](https://res.cloudinary.com/thewebmaster/image/upload/images/blog/jpeg-images-definitive-guide/quantized-DCT-coefficients.svg)
Now only 20 cosine functions affect the image, many high frequency components have been rounded to zero. This reduces the JPEG file size. This quantization is also lossy.
![[Pasted image 20260421170444.png]]
