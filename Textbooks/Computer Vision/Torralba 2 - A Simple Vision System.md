**2.1 Introduction**
In the 1960s we were way to optimistic for building a vision system.

**2.2 A Simple World: The Blocks World**
A world composed of flat surfaces that can be horizontal or vertical that can be built by cutting, folding, and gluing.

**2.3 A Simple Image Formation Model**
A simple form of projection is parallel/orthographic projection. This type of projection produces images in which objects od not change size as they move closer or farther from the camera, and parallel lines in 3D remain parallel in the 2D image.

![[Pasted image 20260609120346.png]]

(b) can be described by parallel projection.

To generate images described by parallel projection is to use camera zoom, increasing the distance between the camera and the object while zooming, keeps the same approximate image size of the objects, but with reduced perspective effects.

Characterize how a point in world coordinates (X, Y, Z) projects into the image plane. The camera center is at X = 0, the x axis of the camera is parallel to the ground plane (Y = 0). The camera is tilted so the z and x are perpendicular. Angle $\theta$ is the angle between the tilted camera and the Z-axis. The image is parameterized by coordinates $(x, y)$. Z is equal to Y besides a sign change and a scaling.

![[Pasted image 20260609174118.png]]

In this projection model, the world point $(0,0,0)$ projects into $(0,0)$. The resolution or number of pixels also affects the transformation from world coordinates to image coordinates via a constant factor $\alpha$ and that this constant is $\alpha=1$ (for now we are assuming the pixels are square). After these assumptions the transformation between world coordinates and image coordinates 