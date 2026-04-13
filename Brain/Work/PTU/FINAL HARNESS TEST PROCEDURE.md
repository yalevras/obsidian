192.168.8.32 beaglebone

Open 3 terminals
Terminal 1: 
In ~/data/odesa/nsp-tool
python3 s2ser.py /dev/ttyUSB0 1234
Terminal 2:
In ~/data/odesa/nsp-tool
python3 nspcon.py 1234  
- ni=start(1234)
- ni.ping(nsp=1)
Terminal 3:
minicom -D /dev/ttyUSB1 -b 460800


192.168.8.61

in /mnt/data/binaries
./pcdu_init
./pcdu_toggle_channel -b 0 -c 11 -e 1
./pcdu_toggle_channel -b 0 -c 12 -e 1
./pcdu_toggle_channel -b 1 -c 11 -e 1
./pcdu_toggle_channel -b 1 -c 12 -e 1
./pcdu_toggle_channel -b 1 -c 3 -e 1
./pcdu_tlm -b 1 -c 3 -t v
./nisa_ident -a 19 -d /dev/HazCam
to make sure we can communicate with the camera`