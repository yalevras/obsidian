https://arxiv.org/pdf/2507.12132

CSI - Channel State Information
HAR - Human Activity Recognition
NeRF - Neural Radiance Fields
	- which learn a volumetric representation of a 3D scene from 2D images
OFDM - Orthogonal Frequency-Division Multiplexing: a digital method that splits a single wide-band signal into dozens or thousands of smaller, closely spaced sub-signals

DoRF - Doppler Radiance Field
	- Proposal is to reconstruct a 3D latent motion representation from 1D Doppler velocity projections extracted from Wi-Fi CSI
	- Issues, current advances, generalizability remains insufficient for practical deployment

Wi-Fi sensing unlike cameras does not record identifiable visual information, leading to improved privacy.

Wi-Fi based HAR estimates human motion by analyzing how it alters the wireless channel through CSI. CSI reflects signal modifications due to reflections and scattering. Machine learning is used with the magnitude or phase of CSI.
	- Magnitude-based methods work best in static settings but are sensitive to environmental c hanges
	- Phase-based methods suffer from phase wrapping and hardware noise.

Alternative approaches extract Doppler velocity capturing frequency shifts from motion while suppressing static structures. Most methods estimate a single velocity by aggregating all multipath components.

MORIC, a new development extracts multiple Doppler projects interpreted as views from virtual cameras distributed on a sphere.

Wait this is cool so the multipath angles are really just different camera viewpoints.

Each camera represents the net effect of multipaths modelled by a von Mises-Fisher distribution, enabling a more structured view of motion and allowing for high-level activity features with raw CSI.
![[Pasted image 20260604233004.png]]

The random nature of environmental reflections causes the viewing angles of each Wi-FI access point (AP) to be limited and variable over time, hindering uniform coverage of the motion space making it challenging to synchronize observations across trials (we're going to need to estimate some of these APs potentially).

This is analogous to viewing a 3D object through a few 2D image (something artificial we can put in the room that splits the signal into more paths).

DoRF heavily improves on this. 

**2. Delay-Doppler Decomposition of CSI**

