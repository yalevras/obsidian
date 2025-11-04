
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
4. Turn on the IMU and start sampling
	1. Power on the IMU
		1. (1)
	2. Open connection to the IMU
		1. (5)
	3. Enable sampling on the IMU
5. Turn on the EKF and wait until the bias is updated
	1. Start EKF
6. Turn on OD
	1. Turn on OD
		1. (3)
	2. Turn on Haz OD
7. Turn on VO
	1. Turn on VO
		1. (5)
8. Drive
							43 TOTAL SECONDS?!!!!! (nuh uh)
							-18 from leaving cameras on
9. Stop VO, OD, disconnect from IMU and turn it off
10. Stop EKF
11. Take a navigation image on Port Stereo, if needed
12. Turn off the cameras