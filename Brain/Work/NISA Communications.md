![[Pasted image 20251028095859.png]]
Flatsat
NISA UTILITIES:
HKOBC:
	./nisa-ident -a 16 -d /dev/StarboardStereoCam

MISST
NISA UTILITIES:
HKOBC:
	microcom -s 921600 /dev/ttyUSB0     <- Port Pano
	microcom -s 921600 /dev/ttyUSB1     <- Port Stereo
	microcom -s 921600 /dev/ttyUSB2     <- Starboard Stereo
	./nisa-ident -d /dev/StarboardStereoCam
	camera version 54.3
	