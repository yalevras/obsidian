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
			- use_variable_time_step - enables CFL-based adaptive timestepping; the solver shrinks/grows the step automatically to stay stable
		- setgravity for sph particles
		- setgravity for mbs for wheel rigid body
		- sph set spacing
		- sph set kernel
		- fsi set step size cfd
		- mbs set collision system type
		- cuda error checking is on
		- tire deformation solver

createsoilbox

define bce frame, position, angle?
	chframe is a position and orientation in space

initialize each wheel
	Show more
	2:27 PM
	The Wheel Body (Always Created)
	cpp
	wm.wheel_body = chrono_types::make_shared<ChBody>();
	wm.wheel_body->SetPos(wm.current_pos);
	wm.wheel_body->SetMass(wm.wheel.chassis_mass);
	sim.sysMBS.AddBody(wm.wheel_body);
	This is the rigid hub — always exists regardless of tire deformation mode. It lives in sysMBS and is what receives velocity/position inputs from your external controller in DoStep. Think of it as the axle/chassis point the tire hangs off of.
	
	Branch 1 — Deformable Tire
	cpp
	wm.wheel_body->AddAccumulator();
	wm.wheel_mesh = CreateWheelMesh(sim, wm.wheel, prop, wm.wheel_body);
	sim.sysMBS.Add(wm.wheel_mesh);
	sim.sysFSI.AddFsiMesh2D(wm.wheel_mesh, false);
	AddAccumulator() — adds a force/torque accumulator slot to the hub body so your spring-damper node forces in DoStep have somewhere to accumulate to and be read back out.
	
	CreateWheelMesh — builds the ANCF shell mesh, a cylinder of ChElementShellANCF_3423 elements arranged around the wheel radius. These are the deformable nodes.
	
	sysMBS.Add(wm.wheel_mesh) — registers the FEA mesh with the MBS solver so MINRES integrates the node positions every timestep.
	
	AddFsiMesh2D — this is the key FSI coupling call. It tells the FSI system to treat the mesh surface as a deformable BCE boundary. Unlike AddFsiBody which attaches BCE points to a rigid body, AddFsiMesh2D makes BCE markers follow individual FEA nodes — so as the tire deforms, the BCE boundary deforms with it in real time.
	
	The relationships look like:
	
	sysMBS integrates FEA nodes
	         ↓
	AddFsiMesh2D links nodes → BCE markers
	         ↓
	BCE markers move with deformed tire surface
	         ↓
	SPH particles feel the deforming boundary
	Branch 2 — Rigid Tire
	cpp
	wm.wheel_body->SetInertiaXX(ChVector3d(0.5 * wm.wheel.wheel_mass * std::pow(wm.wheel.radius, 2), 1, 1));
	wheel_bce = sim.sysSPH.CreatePointsCylinderInterior(wm.wheel.radius, wm.wheel.length, false);
	sim.sysFSI.AddFsiBody(wm.wheel_body, wheel_bce, bce_frame, false);
	SetInertiaXX — sets the rotational inertia of a solid cylinder (0.5 * m * r² is the formula for a cylinder rotating about its axis). The Y and Z components are just 1 as placeholders since rotation is mostly about X for a rolling wheel.
	
	CreatePointsCylinderInterior — generates a 3D cloud of points filling the cylinder volume. These become the BCE markers.
	
	AddFsiBody — attaches those BCE points rigidly to wheel_body with the frame transformation applied. Since there's no FEA mesh, BCE markers all move together as one rigid unit following the hub body.
	
	The relationships look like:
	
	sysMBS integrates wheel_body (rigid)
	         ↓
	AddFsiBody links wheel_body → BCE markers move rigidly
	         ↓
	SPH particles feel a non-deforming cylinder boundary
	Key Difference Between the Two
	Deformable	Rigid
	BCE follows	Individual FEA nodes	Rigid hub body as one unit
	SPH sees	Deforming tire surface	Fixed cylinder shape
	MBS solves	Hub + FEA nodes	Hub only
	FSI call	AddFsiMesh2D	AddFsiBody
	Force feedback	Per-node via spring-damper	Per-body via GetFsiBodyForce