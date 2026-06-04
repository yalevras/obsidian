chcontactmaterialsmc/h
chbodyeasy.h


namespace chrono fsi,fea,fsi sph
 fea - finite element analysis (simulation of how structures react to real-world forces like stress, vibration, and heat)
 fsi - fluid solid interaction
 sph - smoothed particle hydrodynamics

cudaSetDevice(0) - sets which gpu the current cpu thread should use, told to the cuda runtime

make particle and frames directories
	- what does particle directory do

set variable for wheel_radius and wheel_length

define computational domain, different than the active domain, computational domain 
ChAABB - Axis-Aligned Bounding Box
cMin and cMax are two corners of this box
BC_NONE - boundary conditions
	- we use none, but there is also PERIODIC for wrap around behaviour, or INLET OUTLET where fluid can leave one side and reenter the other side

ConfigureSystems(sim,soil,prop)
	- configure granular material properties, SPH parameters, and other simulation parameters
			- zsim soil prop
		- define material properties of soil
			- density, mass per unit volume of soil particles
			- youngs_modulus