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
			- youngs_modulus, stiffness-resistance to elastic deformation
			- poisson ratio - how much it bulges sideways when compressed
			- rheology_model - uses mu i rheology model, a well-established granular flow model where friction depends on how fast particles are shearing relative to pressure
			- mu_io - reference intertial number, controls the transition beween slow/fast flow regimes
			- mu_fric_s - static friction coefficient
			- mu_fric_2 - dynamic friction coefficient
			- average_diam - average grain size, affects the inertial number calculation
			- cohesion_coeff - how much the soil sticks to things
		- define sph properties
			- these control how the simulation is computed
			- integration scheme
			- distance between sph particles at init
			- kernel smoothing
			- kernel type blah
			- artificial_viscosity - numerical damping to prevent particle interpenetration and stabilize shock
			- viscosity_method - ARTIFICIAL_BILATERAL, applies viscosity symmetrically between particle pairs
			- boundary_method - HOLMES, how BCE boundary particles enforce the no-penetratoin condition
			- particle shifting
				- shifting_method - PPST_XSPH, combines two methods together
				- settings for these
			- free_surface_threshold - neighbour count below this flags a particle as a free surface, affecting force calculations
			- num_proximity_search_steps - how often the neighbor list is rebuilt, 1 = every step
			- use_variable_time_step 