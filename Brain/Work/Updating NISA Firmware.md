
Get into OBC .62 (easier if you go in over ethernet because we have to do some file transfers and it will just be faster)
IPv4
192.168.0.50
255.255.255.0
192.168.0.100
???

./pcdu_init
./pcdu_toggle_channel -b 0 -11 -e 1
.
.
.
regulators
./pcdu_toggle_channel -b 0 -c 5 -e 1
diff update to the firmware, not a clean install of the firmware
diff updates are a binary diff file for all of the things to change in the filesystem to make it the newer version. checks the integreity of the read oply protion of the camera. if you have changed something to be read write and you try to diff update it, it comes up with an issue.

double check version
this transfer is from 54.3 to 54.4
2. production
2 
nisa
7
1
4
on dropbox

transfer the update file

set the current time (needed for the diff update)
set the time both on the obc and the camera itself
date MMDDHHmmYYYY
then ./nisa-set-time -d /dev/MSICam -a 21
check date command on nisa
upload the update file to /tmp/(difffile)
./nisa-apply-update -d /dev/MSICam -a 21 /tmp/(difffile)
