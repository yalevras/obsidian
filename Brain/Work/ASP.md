Compiling asp:

make cfs like normal

cd .. ← so you’re in cfs_draco/build

cd arm-cortexa8_neon-linux-gnueabi/

cd cpu1_lrm/

cd apps

cd asp

cp asp_script_api.aspec ~/yanni/scripts/

cd ~/yanni/scripts

cd obc

cp messages/* .

ln -s ../asp_script_api.aspec

ls -l ← double check symbolic link is made

aspc asp_script_api.aspec init_script.asp (and load_comms_tbls.asp, init_cams.asp, take_img.asp, take_img_full.asp, drive_lrm.asp, waypoint_drive.asp

cp *.aspe ../../cfs_draco/build/exe/cpu1/cf/

cd ../../cfs_draco/build/exe

tar -czf cpu1.tar.gz cpu1/

IF SYMBOLIC LINK ISN’T MADE

cd .. && cd arm-cortexa8_neon-linux-gnueabi/cpu1_lrm/apps/asp && cp asp_script_api.aspec ~/yanni/scripts/ && cd ~/yanni/scripts/obc && cp messages/* . && ln -s ../asp_script_api.aspec && ls -l && aspc asp_script_api.aspec init_script.asp && aspc asp_script_api.aspec load_comms_tbls.asp && aspc asp_script_api.aspec init_cams.asp && aspc asp_script_api.aspec take_img.asp && aspc asp_script_api.aspec take_img_full.aso && aspc asp_script_api.aspec drive_lrm.asp && aspc asp_script_api.aspec waypoint_drive.asp && cp *.aspe ../../cfs_draco/build/exe/cpu1/cf/ && cd ../../cfs_draco/build/exe && tar -czf cpu1.tar.gz cpu1/

IF SYMBOLIC LINK IS MADE

cd .. && cd arm-cortexa8_neon-linux-gnueabi/cpu1_lrm/apps/asp && cp asp_script_api.aspec ~/yanni/scripts/ && cd ~/yanni/scripts/obc && cp messages/* . && aspc asp_script_api.aspec init_script.asp && aspc asp_script_api.aspec load_comms_tbls.asp && aspc asp_script_api.aspec init_cams.asp && aspc asp_script_api.aspec take_img.asp && aspc asp_script_api.aspec take_img_full.asp && aspc asp_script_api.aspec drive_lrm.asp && aspc asp_script_api.aspec waypoint_drive.asp && cp *.aspe ../../cfs_draco/build/exe/cpu1/cf/ && cd ../../cfs_draco/build/exe && tar -czf cpu1.tar.gz cpu1/

Sbn defaults to NSP so we need to remove symbolic link and create a new one to use UDP. In cpu1 and 2 /cf

- rm sbn_conf_tbl.tbl
- ln -s sbn_conf_tbl-UDP.tbl sbn_conf_tbl.tbl

rm sbn_conf_tbl.tbl && ln -s sbn_conf_tbl-UDP.tbl sbn_conf_tbl.tbl && cd .. && ./core-cpu1

rm sbn_conf_tbl.tbl && ln -s sbn_conf_tbl-UDP.tbl sbn_conf_tbl.tbl && cd .. && ./core-cpu2

100 200 200 100 0 4095 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0 1.0

Drive mode:

d - distance drive

a - angle drive

t -time drive

**Drive_lrm.asp improvements and testing**

Notes:

- failure to set EKF bias

Init MCU

2

Enable motor commands

Power cycle cams if vo, od, or nav is on

18

Load com tables

Validate

Activate

5

Set Time

2

Auto exp commands

2

Send QueryHealth

Turn on IMU

…

Turn on EKF and wait

if od: od enable 3

if vo: vo enable

5

drive modes

disable vo

1

disable od

1

stop ekf

10

if nav && haz

power cycle cams

20

Init MCU

_Power cycle cams if vo, od, or nav is on_

_Turn on IMU_

…

_Turn on EKF and wait_

2

Enable motor commands

16

Load com tables

Validate

Activate

5

Set Time

2

Auto exp commands

2

Send QueryHealth

if od: od enable 3

if vo: vo enable _5_

drive modes

disable vo

1

disable od

1

stop ekf

10

if nav && haz _&& mode_od ←this should only need to power cycle cams if nisa app needs to be reset which would only happen if od is turned on_

power cycle cams

**Take_img_full.asp improvements and testing**

- CFS event services

ANY NISA COMMAND YOU ARE GOING TO RECEIVE YOU WILL RECEIVE 2 ACKS, have two waits

![[Pasted image 20250922111807.png]]

**Summary of Past Two Weeks:**

NISA Bug Fixes:

- busy flags not reset issue not able to be replicated, but a fix is implemented
- high exposure times now work with the increase of a timeout offset by 599 extra ms. source of this extra time is not within cfs code, assumed to be a nisa camera software feature? (i talked to allen about it and he was not sure, he pointed me to don, but either way changing this is probably out of scope?)
- i was not able to figure out how to actually download these pointclouds but currently the code will send the pointclouds to a /cf/pointcloud directory, just not sure how to fully test this
- download file by name i need some assisstance with
- nisa double asp acknowledgements currently being tested with asp changes in the take_img_full.asp script
- a lot of time in the past two weeks was spent with nathan showing me everything about using the edu rover and how asp works and compiles
- for the drive_lrm.asp script, i have a plan for rearranging the script that should save 7 seconds if od is enabled, 22 seconds if vo is enables, and 2 seconds if both
- i have helped mitchell a bit with some cfs and yamcs issues he was having with misst
- the mount for the last camera test with andreas is made, but when i helped mariia do the testing last time, i did not have any of the commands or locations of where i should save data, and was also not 100% sure about the setup as well as how to calibrate the sensors in the curtain room

![[Pasted image 20250922111755.png]]



Regression testing
Fuzz testing

Calling C from Python

Libaspe.so is the engine

kwargs

symbols in python

subset test

python multidimensional arrays

