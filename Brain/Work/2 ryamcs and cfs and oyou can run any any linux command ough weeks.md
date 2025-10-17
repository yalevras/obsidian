
configuratble rolling buffers for telemetry being saved in ds (data storage app).

table entries have pathname basename extension etc.....
maxfilesize and maxfileage, once you reach either that size in bytes or has been opened for this many sections, it will close, wirte to the fiole system and close it. and open a new one. WE WANT A TABLE PARAMETER AND PER ENTRY TO BE ABLE TO SPECIFY a length of time maybe a number of bytes for after so long delete the older data (probably anumber of btes).for each app and science instrument you have this many megabytes in space. each gets a certain block of bugger space for telemetry









app called deb (debug app) it is one file, it runs a bash session th

through hamcs you can run anything like from nisa-execute-command.

make it so that this bash shell is running as a different user, so that any time we are trying to run a certain command, put you into a different mode so that you are able to run the command
OR a table with restricted command








fm unit tests are DOEN but we dont know if they work (we think they do)
cf ds and fm we have made changes to, check all of the nasa app unit tests and see if they are all good









imu currently supports a bunch of different data rates. we run it at the slowed data rate. there exists a  command to set a data rate.. currently we run at 125 hz?

we were reading slower than it would output and there would be issues

it should be fine now which is why we picked this. it would be good to know or just support the sensor if theres any problems using a new data rate. check the imu cfs code, potentially change the rate at which things are read or buffer sizes, does it overwhelm imu cpu usage, serial drivers?
max 15 measures at a time 10 hz (should be getting 12.5 per second)












locomotion when you run with nsp
error enqueing packet -9
nsp has queue depth from other apps to dump on the bus. has a timeout period. time to talk to the mcu

we are sending small command, should be round trip exceedingly quick so we shouldnt be dropping packets on that front
i think the queue depth is 10 command and at 10 hz we do all these things we a re probably sending like 12 commands to it at a time and they are just dropping a few every few seconds









nisa-app




nisa camera interruption script
what the nisa raw command structure is gonna look like 
talk to allen
how fclose to the end of the fixed time bootup cn we iterrupt that. if we can get that script written so we can acgtually do that





