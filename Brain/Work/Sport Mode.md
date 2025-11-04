
Making the drive script faster where we can

1. Power on the MCU and arm it
	1. Power on MCU
		1. (2)
	2. Enable motor commands
2. Power cycle Haz Cam, Star Stereo, and Port Stereo if we're using VO or OD
	1. Turn off 3 cams
		1. (1)
	2. Turn on 3 cams
3. Configure the cameras if we're using VO or OD
	1. Load camera table
		1. (2)
	2. Validate camera table
		1. (18)
	3. Activate camera table
		1. (2)
	4. Set time
		1. (2)
	5. Set autoexp
		1. (2)
	6. Send query health
5. Turn on the IMU and start sampling
6. Turn on the EKF and wait until the bias is updated
7. Turn on VO
8. Turn on OD
9. Drive
10. Stop VO, OD, disconnect from IMU and turn it off
11. Stop EKF
12. Take a navigation image on Port Stereo, if needed
13. Turn off the cameras