192.168.8.32 beaglebone

Open 3 terminals
Terminal 1: 
python3 s2ser.py /dev/ttyUSB0 1234
Terminal 2:
python3 nspcon.py 1234  
- ni=start(1234)
- ni.ping(nsp=1)
Terminal 3:
minicom -D /dev/ttyUSB1 -b 460800


192.168.8.61

csp-tool