**2.1 Introduction**
In the 1960s we were way to optimistic for building a vision system.

**2.2 A Simple World: The Blocks World**
A world composed of flat surfaces that can be horizontal or vertical that can be built by cutting, folding, and gluing.

**2.3 A Simple Image Formation Model**
A simple form of projection is parallel/orthographic projection. This type of projection produces images in which objects od not change size as they move closer or farther from the camera, and parallel lines in 3D remain parallel in the 2D image.

![[Pasted image 20260609120346.png|660]]

(b) can be described by parallel projection.

To generate images described by parallel projection is to use camera zoom, increasing the distance between the camera and the object while zooming, keeps the same approximate image size of the objects, but with reduced perspective effects.

Characterize how a point in world coordinates $(X, Y, Z)$ projects into the image plane. The camera center is at $X = 0$, the $X$-axis of the camera is parallel to the ground plane ($Y = 0$). The camera is tilted so the $Z$ and $X$ are perpendicular. Angle $\theta$ is the angle between the tilted camera and the $Z$-axis. The image is parameterized by coordinates $(x, y)$. $Z$ is equal to $Y$ besides a sign change and a scaling.

![[Pasted image 20260609174118.png|624]]

In this projection model, the world point $(0,0,0)$ projects into $(0,0)$. The resolution or number of pixels also affects the transformation from world coordinates to image coordinates via a constant factor $\alpha$ and that this constant is $\alpha=1$ (for now we are assuming the pixels are square). After these assumptions the transformation between world coordinates and image coordinates is:
$$x=X$$
		$$y=cos(\theta)Y-sin(\theta)Z$$
With this parameterization the world coordinates $Y$ and $Z$ are mixed after projection. From the camera, a point moving parallel to the $Z$-axis will be indistinguishable from a point moving parallel to the $Y$-axis.

**2.4 A Simple Goal**
We want to recover the world coordinates of all the pixels seen by a camera.

**2.5 From Images to Edges and Useful Features**
The below image is the function $l(x,y)$ that outputs the intensity at a location $(x,y)$. The image is an array of intensity values (color values) indexed by location. The direction of each light ray in the world is well defined,
![[Pasted image 20260610162146.png|626]]

**2.5.1 A Catalog of Edges**
Edges can have variations due to scene factors shown below.
![[Pasted image 20260611135339.png|431]]
We want to classify image edges according to their most probable cause. The following are image boundaries.
	**Object boundaries:** indicate pixels that delineate the boundaries of any object, which usually correspond to changes in surface color, texture, and orientation.
	**Surface orientation:** changes in this indicate locations where there are image variations, with a change in the image intensity which is a function of the angle between the surface and the incident light.
	**Shadow edges:** this is typically harder, but here, shadows are soft with slow transitions
The following are object boundaries.
	**Contact edges:** a boundary between two object that are touching, therefore no depth discontinuity
	**Occlusion boundaries:** this happens when an object is partially in front of another, generally producing depth discontinuities. In the above image, objects don't occlude each other but they do occlude the background.

