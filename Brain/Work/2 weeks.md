
- DS app "rolling buffer" functionality
	- configuratble rolling buffers for telemetry being saved in ds (data storage app).
	- table entries have pathname basename extension etc.....
	- maxfilesize and maxfileage, once you reach either that size in bytes or has been opened for this many sections, it will close, wirte to the fiole system and close it. and open a new one. WE WANT A TABLE PARAMETER AND PER ENTRY TO BE ABLE TO SPECIFY a length of time maybe a number of bytes for after so long delete the older data (probably anumber of btes).for each app and science instrument you have this many megabytes in space. each gets a certain block of bugger space for telemetry
- debug application "extra safety" for certain commands? Maybe making the user not operate as "root" so they can't accidentally break things?
	- app called deb (debug app) it is one file, it runs a bash session through yamcs and cfs and oyou can run any any linux command
	- through hamcs you can run anything like from nisa-execute-command.
	- make it so that this bash shell is running as a different user, so that any time we are trying to run a certain command, put you into a different mode so that you are able to run the command
	- ~~OR a table with restricted command~~
		- CURRENT SOLUTION:
			- table filters list of dangerous commands
- Look at making some of the apps that already have unit tests written "comprehensive" or see if they run in general  
	- CF app  
	- Data storage app  
	- Health and safety app  
	- SBN app  
	- File manager app  
	- comms app (will likely need some modifications since this is an amalgamation of a few apps)
	- fm unit tests are DOEN but we dont know if they work (we think they do)
	- cf ds and fm we have made changes to, check all of the nasa app unit tests and see if they are all good
- Test OBC cpu usage when setting the IMU to higher output rates
	- imu currently supports a bunch of different data rates. we run it at the slowed data rate. there exists a  command to set a data rate.. currently we run at 125 hz?
	- we were reading slower than it would output and there would be issues
	- it should be fine now which is why we picked this. it would be good to know or just support the sensor if theres any problems using a new data rate. check the imu cfs code, potentially change the rate at which things are read or buffer sizes, does it overwhelm imu cpu usage, serial drivers?
	- max 15 measures at a time 10 hz (should be getting 12.5 per second)
- Locomotion app dropped NSP packet when talking to the MCU
	- locomotion when you run with nsp
	- error enqueing packet -9
	- nsp has queue depth from other apps to dump on the bus. has a timeout period. time to talk to the mcu
	- we are sending small command, should be round trip exceedingly quick so we shouldnt be dropping packets on that front
	- queue depth is 10 commands and at 10 hz we do all these things we a re probably sending like 12 commands to it at a time and they are just dropping a few every few seconds
- nisa camera interruption script
	- what the nisa raw command structure is gonna look like 
	- talk to allen
	- how fclose to the end of the fixed time bootup cn we iterrupt that. if we can get that script written so we can actually do that





