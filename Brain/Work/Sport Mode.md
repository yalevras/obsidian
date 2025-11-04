
Making the drive script faster where we can

1. Power on the MCU and arm it
	1. Power on MCU
		1. (2)
	2. Enable motor commands
2. Power cycle Haz Cam, Star Stereo, and Port Stereo if we're using VO or OD
	1. Turn off 3 cams
		1. (1)
	2. Turn on 3 cams
	3. Load camera table
		1. (2)
	4. Validate camera tab
3. Configure the cameras if we're using VO or OD
4. Turn on the IMU and start sampling
5. Turn on the EKF and wait until the bias is updated
6. Turn on VO
7. Turn on OD
8. Drive
9. Stop VO, OD, disconnect from IMU and turn it off
10. Stop EKF
11. Take a navigation image on Port Stereo, if needed
12. Turn off the cameras