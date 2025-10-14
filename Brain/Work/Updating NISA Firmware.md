
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
diff updates are a binary diff file for all of the things to change in the fi