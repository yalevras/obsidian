![[Pasted image 20251028095859.png]]
Flatsat
NISA UTILITIES:
HKOBC:
	./nisa-ident -a 16 -d /dev/StarboardStereoCam

MISST
NISA UTILITIES:
HKOBC:
	microcom -s 921600 /dev/ttyUSB0     <- Port Pano
	./nisa-ident -d /dev/StarboardStereoCam
	camera version 54.3