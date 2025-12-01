![[Pasted image 20251201170317.png]]
Flatsat
NISA UTILITIES:
HKOBC:
	./nisa-ident -a 16 -d /dev/StarboardStereoCam

MISST
NISA UTILITIES:
HKOBC:
	microcom -s 921600 /dev/ttyUSB0     <- Port Pano
	microcom -s 921600 /dev/ttyUSB1     <- Port Stereo
	microcom -s 921600 /dev/ttyUSB2     <- Starboard Stereo     <----- doesn't work
	./nisa-ident -d /dev/StarboardStereoCam
	./nisa-execute-command -d /dev/StarboardStereoCam "ls -l /data/upload"

	camera version 54.3



PortPano seems to be con