
Making the drive script faster where we can

Power on the MCU and arm it
Power cycle Haz Cam, Star Stereo, and Port Stereo if we're using VO or OD
Configure the cameras if we're using VO or OD
Turn on the IMU and start sampling
Turn on the EKF and wait until the bias is updated
Turn on VO
Turn on OD
Drive
Stop VO, OD, disconnect from IMU and turn it off
Stop EKF
Take a navigation image on Port Stereo, if needed
Turn off the cameras