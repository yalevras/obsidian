ftpput -u root -p root -P 21 10.0.0.1 /yanni/cpu1.tar.gz /mnt/data/data/yanni/cpu1.tar.gz

ftpput -u root -p root -P 21 10.0.0.2 /yanni/cpu2.tar.gz /mnt/data/data/yanni/cpu2.tar.gz

ftpput -u root -p root -P 21 10.0.0.2 /yanni/msi_img_data_full.aspe /mnt/data/data/yanni/msi_img_data_full.aspe

make distclean && make prep && make && make install && cd build/exe && tar -czf cpu1.tar.gz cpu1/ && tar -czf cpu2.tar.gz cpu2/

export ASP_INCLUDE=/usr/local/include/asp:/home/canadensys/yanni/scripts/obc/messages:/home/canadensys/yanni/scripts/nisa/msi

make distclean && make ENABLE_UNIT_TESTS=true prep && make install && cd build/exe && tar -czf cpu1.tar.gz cpu1/ && tar -czf cpu2.tar.gz cpu2/

make ENABLE_UNIT_TESTS=true prep make make install

./pcdu_tlm -b 0 -c 2 -t v && ./pcdu_tlm -b 0 -c 3 -t v && ./pcdu_tlm -b 1 -c 3 -t v && ./pcdu_tlm -b 1 -c 4 -t v && ./pcdu_tlm -b 1 -c 5 -t v

make distclean && make prep && make && make install && cd build/exe && tar -czf cpu1.tar.gz cpu1/ && tar -czf cpu2.tar.gz cpu2/ && cd .. && cd arm-cortexa8_neon-linux-gnueabi/cpu1_lrm/apps/asp && cp asp_script_api.aspec ~/yanni/scripts/ && cd ~/yanni/scripts/obc && cp messages/* . && aspc asp_script_api.aspec init_script.asp && aspc asp_script_api.aspec load_comms_tbls.asp && aspc asp_script_api.aspec init_cams.asp && aspc asp_script_api.aspec take_img.asp && aspc asp_script_api.aspec take_img_full.asp && aspc asp_script_api.aspec drive_lrm.asp && aspc asp_script_api.aspec waypoint_drive.asp && cp *.aspe ../../cfs_draco/build/exe/cpu1/cf/ && cd ../../cfs_draco/build/exe && tar -czf cpu1.tar.gz cpu1/

make distclean && make prep && make && make install && cd build/exe && tar -czf cpu1.tar.gz cpu1/ && tar -czf cpu2.tar.gz cpu2/ && cd .. && cd arm-cortexa8_neon-linux-gnueabi/cpu1_lrm/apps/asp && cp asp_script_api.aspec ~/yanni/scripts/ && cd ~/yanni/scripts/obc && cp messages/* . && aspc asp_script_api.aspec init_script.asp && aspc asp_script_api.aspec load_comms_tbls.asp && aspc asp_script_api.aspec init_cams.asp && aspc asp_script_api.aspec take_img.asp && aspc asp_script_api.aspec take_img_full.asp && aspc asp_script_api.aspec drive_lrm.asp && aspc asp_script_api.aspec waypoint_drive.asp && aspc asp_script_api.aspec msi_parse_data.asp && aspc asp_script_api.aspec msi_img_data_full.asp && cp *.aspe ../../cfs_draco/build/exe/cpu1/cf/ && cd ../../cfs_draco/build/exe && tar -czf cpu1.tar.gz cpu1/

cd ../../../scripts/obc && aspc asp_script_api.aspec msi_img_data_full.asp && cp *.aspe ../../cfs_draco/build/exe/cpu1/cf/ && tar -czf ../../cfs_draco/build/exe/cpu1.tar.gz cpu1/

asp log can be found in /tmp/script.log

export ASP_INCLUDE=/usr/local/include/asp:/home/canadensys/yanni/scripts/obc/messages:/home/canadensys/yanni/scripts/nisa/msi

gives you networking information and socket port numbers

lsof -i -n -P | grep core-cpu2

open .29

telnet 40.40.40.3

run ./ftpserver in /mnt/data/data on obc1

cd /yanni/edu_rover/upload

on .29 do ftp 40.40.40.3

enter

cd yanni

put cpu1.tar.gz

put cpu2.tar.gz

run ./ftpserver on obc2

ftpput -u root -p root -P 21 10.0.0.2 /yanni/cpu2.tar.gz /mnt/data/data/yanni/cpu2.tar.gz

/log/messages.1.gz ← look for most recent timestamp

gunzip messages.1.gz

set imaging sensor on nisa

./nisa-set-param -a 21 -d /dev/MSIcam -f uint8 2 6 0

if ./nisa-get-param -a 21 -d /dev/MSIcam -f uint 2 6 returns 0, then the imager is on, if 1, off

OSAL CHANGE TO SEE WHERE THINGS WENT WRONG:

change in os-impl-posix-dl-loader.c

OS_DEBUG(”Error loading shared library: %s\n”, dlerror());

to printf


192.168.0.2

ethernet debug port
telnet 192.168.0.100
puts me on payload
telnet 10.0.0.1
then conf



![[Pasted image 20250929084419.png]]