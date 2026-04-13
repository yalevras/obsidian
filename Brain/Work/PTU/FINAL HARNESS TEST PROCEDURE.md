192.168.8.32 beaglebone

NSP Testing:
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

CSP Testing:
in ~/data/ptu/sw_nisa-cam_utils

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
to make sure we can communicate with the camera



1970-1-1 0:5:19 ERROR > UART_INT_Handler[/home/debian/data/odesa/fw_odesa_commor
1970-1-1 0:5:19 ERROR > UART_INT_Handler[/home/debian/data/odesa/fw_odesa_commorv/

1970-1-1 0:6:52 ERROR > UART_INT_Handler[/home/debian/data/odesa/fw_odesa_common/platform/samv71/apps/common/source/usar
1970-1-1 0:6:52 ERROR > UART_INT_Handler[/home/debian/data/odesa/fw_odesa_common/platform/samv71/apps/common/source/usar


1970-1-1 0:7:12 ERROR > UART_INT_Handler[/home/debian/data/odesa/fw_odesa_common/platform/samv71/apps/common/source/usart_ctrl.c:183] :serial frame error
1970-1-1 0:7:12 ERROR > UART_INT_Handler[/home/debian/data/odesa/fw_odesa_common/platform/samv71/apps/common/source/usart_ctrl.c:175] :serial overrun error

could do csp then nsp then csp and still talk to camera, need to check dmesg still

could not do nsp then csp then nsp again


