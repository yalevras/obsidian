https://arxiv.org/pdf/2507.12132

CSI - Channel State Information
HAR - Human Activity Recognition
NeRF - Neural Radiance Fields
	- which learn a volumetric representation of a 3D scene from 2D images

DoRF - Doppler Radiance Field
	- Proposal is to reconstruct a 3D latent motion representation from 1D Doppler velocity projections extracted from Wi-Fi CSI
	- Issues, current advances, generalizability remains insufficient for practical deployment

Wi-Fi sensing unlike cameras does not record identifiable visual information, leading to improved privacy.

Wi-Fi based HAR estimates human motion by analyzing how it alters the wireless channel through CSI. CSI reflects signal modifications due to reflections and scattering. Machine learning is used with the magnitude or phase of CSI.
	- Magnitude-based methods work best in static settings but are sensitive to environmental c hanges
	- Phase-based methods suffer from phase wrapping and hardware noise.

