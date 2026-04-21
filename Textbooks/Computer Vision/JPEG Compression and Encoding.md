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
![Contrast sensitivity of the eye.](https://res.cloudinary.com/thewebmaster/image/upload/images/blog/jpeg-images-definitive-guide/contrast_sensitivity_of_the_eye.svg)

