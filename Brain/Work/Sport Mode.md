
Making the drive script faster where we can put things to sleep to resume after
In gnc_nisa_mgr.c, add a new mode for waiting/pause.

VO_Enable enables vo cycles to start running while VO_Single just runs one VO capture

Add a parameter in GNC_NISA_MGR_SharedData to know if we want to pause after

When do we actually want to induce this pausing? Be able to VO_disable and reenable without returning things on

case GNC_NISA_MGR_VO_PAUSE:

1. Power on the MCU and arm it
	1. Power on MCU
		1. (2)
	2. Enable motor commands
2. Power cycle Haz Cam, Star Stereo, and Port Stereo if we're using VO or OD
	1. Turn off 3 cams
		1. ==(1)==
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



Path Safe Slope: 0.000000
Path Safe Unknown Area: 0.000000
Confidence: 0.352116
Rover position in MAP: -0.002950, -3.160385, 0.129938
Map Min: -2.512500, Map Res: 0.025000, Map Width: 201
Setting near edge to 0.647885 because -2.512500 and -3.160385
Setting far edge to 5.672885 because 0.647885 and 0.025000
Sending to locomotion app: 0.647885 near edge, 5.672885 far edge
EVS Port1 66/1/CFE_SB 25: Pipe Overflow,MsgId 0x880,pipe SBN_2_66_Pipe,sender COMMS_APP.COMMS_TO_TASK
EVS Port1 66/1/CFE_SB 25: Pipe Overflow,MsgId 0x8f6,pipe SBN_2_66_Pipe,sender COMMS_APP.LANDER TASK
EVS Port1 66/1/CFE_SB 25: Pipe Overflow,MsgId 0x8e6,pipe SBN_2_66_Pipe,sender TOF_APP
EVS Port1 66/1/NISA 11: Turning camera nav_stereoPort sensor OFF
EVS Port1 66/1/NISA 11: Sequence for camera nav_stereoPort finished
EVS Port1 66/1/NISA 11: Turning camera nav_stereoStarboard sensor OFF
EVS Port1 66/1/NISA 11: Sequence for camera nav_stereoStarboard finished
EVS Port1 66/1/NISA 11: Starting sequence for camera nav_stereoStarboard, fcn 22
EVS Port1 66/1/NISA 11: Starting script /data/upload/star_vo.aspe on camera nav_stereoStarboard with "Do_OD"
EVS Port1 66/1/NISA 11: Starting sequence for camera nav_stereoPort, fcn 22
EVS Port1 66/1/NISA 11: Starting script /data/upload/port_vo.aspe on camera nav_stereoPort with "Do_OD"
Successfully got the data buffer!
valflg_ui8 = 0
img_timestamp_cur_OBT_f64 = 1762282892.270478
img_timestamp_prev_OBT_f64 = 1762282890.250503
ROVpos_RVP_mes_f32[0] = 0.000000
ROVpos_RVP_mes_f32[1] = 0.000000
ROVpos_RVP_mes_f32[2] = 0.000000
ROVq_RVP_mes_f32[0] = 1.000000
ROVq_RVP_mes_f32[1] = 0.000000
ROVq_RVP_mes_f32[2] = 0.000000
ROVq_RVP_mes_f32[3] = 0.000000
res_mes_f32 = 0.000000
EVS Port1 66/1/ASP 12: Engine #0: (1, 2211, 0, '\x04\0\0\0\0\0\0\0')
EVS Port1 66/1/ASP 12: Engine #0: receiving stop flag 0 on try 2
EVS Port1 66/1/NISA 11: Turning camera nav_stereoStarboard sensor OFF
EVS Port1 66/1/NISA 11: Sequence for camera nav_stereoStarboard finished
EVS Port1 66/1/NISA 11: Turning camera nav_stereoPort sensor OFF
Successfully got the data buffer!
valflg_ui8 = 0
img_timestamp_cur_OBT_f64 = 1762282894.150497
img_timestamp_prev_OBT_f64 = 1762282892.270478
ROVpos_RVP_mes_f32[0] = 0.000000
ROVpos_RVP_mes_f32[1] = 0.000000
ROVpos_RVP_mes_f32[2] = 0.000000
ROVq_RVP_mes_f32[0] = 1.000000
ROVq_RVP_mes_f32[1] = 0.000000
ROVq_RVP_mes_f32[2] = 0.000000
ROVq_RVP_mes_f32[3] = 0.000000
res_mes_f32 = 0.000000
EVS Port1 66/1/NISA 11: Sequence for camera nav_stereoPort finished
EVS Port1 66/1/NISA 11: Starting sequence for camera nav_stereoStarboard, fcn 22
EVS Port1 66/1/NISA 11: Starting script /data/upload/star_vo.aspe on camera nav_stereoStarboard with "Do_OD"
EVS Port1 66/1/NISA 11: Starting sequence for camera nav_stereoPort, fcn 22
EVS Port1 66/1/NISA 11: Starting script /data/upload/port_vo.aspe on camera nav_stereoPort with "Do_OD"
.Received file is size: 132 bytes
Successfully got the data buffer!
Receive file is size: 40 bytes
Successfully got the extradata buffer!
Finished receiving value:
Path Safe Roughness: 0.000000
Path Safe Slope: 0.000000
Path Safe Unknown Area: 0.000000
Confidence: 0.000000
Rover position in MAP: -0.002881, -3.771698, 0.129942
Map Min: -2.512500, Map Res: 0.025000, Map Width: 201
Setting near edge to 1.259198 because -2.512500 and -3.771698
Setting far edge to 6.284198 because 1.259198 and 0.025000
Sending to locomotion app: 1.259198 near edge, 6.284198 far edge
EVS Port1 66/1/SCH 18: Multiple slots processed: slot = 29, count = 5
EVS Port1 66/1/NISA 11: Turning camera nav_stereoPort sensor OFF
EVS Port1 66/1/NISA 11: Turning camera nav_stereoStarboard sensor OFF
EVS Port1 66/1/NISA 11: Sequence for camera nav_stereoPort finished
EVS Port1 66/1/NISA 11: Sequence for camera nav_stereoStarboard finished
Successfully got the data buffer!
valflg_ui8 = 0
img_timestamp_cur_OBT_f64 = 1762282896.080509
img_timestamp_prev_OBT_f64 = 1762282894.150497
ROVpos_RVP_mes_f32[0] = 0.000000
ROVpos_RVP_mes_f32[1] = 0.000000
ROVpos_RVP_mes_f32[2] = 0.000000
ROVq_RVP_mes_f32[0] = 1.000000
ROVq_RVP_mes_f32[1] = 0.000000
ROVq_RVP_mes_f32[2] = 0.000000
ROVq_RVP_mes_f32[3] = 0.000000
res_mes_f32 = 0.000000
EVS Port1 66/1/ASP 12: Engine #0: (1, 2211, 0, '\x04\0\0\0\x01\0\0\0')
EVS Port1 66/1/ASP 12: Engine #0: receiving stop flag 1 on try 3
EVS Port1 66/1/ASP 12: Engine #0: Final driving flag is 1, ROVER STOPPED.
EVS Port1 66/1/NISA 11: Starting sequence for camera nav_stereoStarboard, fcn 22
EVS Port1 66/1/NISA 11: Starting script /data/upload/star_vo.aspe on camera nav_stereoStarboard with "Do_OD"
EVS Port1 66/1/NISA 11: Starting sequence for camera nav_stereoPort, fcn 22
EVS Port1 66/1/NISA 11: Starting script /data/upload/port_vo.aspe on camera nav_stereoPort with "Do_OD"
Received file is size: 132 bytes
Successfully got the data buffer!
Receive file is size: 40 bytes
Successfully got the extradata buffer!
Finished receiving value:
Path Safe Roughness: 0.000000
Path Safe Slope: 0.000000
Path Safe Unknown Area: 0.000000
Confidence: 0.000000
Rover position in MAP: -0.002996, -3.771713, 0.129940
Map Min: -2.512500, Map Res: 0.025000, Map Width: 201
Setting near edge to 1.259213 because -2.512500 and -3.771713
Setting far edge to 6.284213 because 1.259213 and 0.025000
Sending to locomotion app: 1.259213 near edge, 6.284213 far edge
Successfully got the data buffer!
valflg_ui8 = 0
img_timestamp_cur_OBT_f64 = 1762282898.370510
img_timestamp_prev_OBT_f64 = 1762282896.080509
ROVpos_RVP_mes_f32[0] = 0.000000
ROVpos_RVP_mes_f32[1] = 0.000000
ROVpos_RVP_mes_f32[2] = 0.000000
ROVq_RVP_mes_f32[0] = 1.000000
ROVq_RVP_mes_f32[1] = 0.000000
ROVq_RVP_mes_f32[2] = 0.000000
ROVq_RVP_mes_f32[3] = 0.000000
res_mes_f32 = 0.000000
EVS Port1 66/1/NISA 11: Turning camera nav_stereoPort sensor OFF
EVS Port1 66/1/NISA 11: Sequence for camera nav_stereoPort finished
EVS Port1 66/1/NISA 11: Turning camera nav_stereoStarboard sensor OFF
EVS Port1 66/1/NISA 11: Sequence for camera nav_stereoStarboard finished
Changing the ROI of the two cameras!!!!!!!!!!!!!!!!!!
.EVS Port1 66/1/SCH 17: Slots skipped: slot = 5, count = 76
EVS Port1 66/1/ASP 12: Engine #0: Receiving in bool: (1, 2264, 0, '\t\0\0\0')
EVS Port1 66/1/ASP 12: Engine #0: Ack got: 9
EVS Port1 66/1/ASP 12: Engine #0: Expecting: 9
EVS Port1 66/1/ASP 12: Engine #0: Success: Safegaurd stop
EVS Port1 66/1/ASP 12: Engine #0: Now sending a tlm msg about script status
EVS Port1 66/1/GNC_NISA_MGR 3: Processing an asp ack command, cc is: 10.

EVS Port1 66/1/GNC_NISA_MGR 2: GNC NISA Manager: VO Disabling
EVS Port1 66/1/GNC_NISA_MGR 2: GNC NISA Manager: Waiting for the process to send an ack.
EVS Port1 66/1/NISA 11: Starting sequence for camera nav_stereoStarboard, fcn 22
EVS Port1 66/1/NISA 11: Starting script /data/upload/vo_reload_lib.aspe on camera nav_stereoStarboard with "/data/settings/lrm/vo_nearROI/"
EVS Port1 66/1/NISA 11: Starting sequence for camera nav_stereoPort, fcn 22
EVS Port1 66/1/NISA 11: Starting script /data/upload/vo_reload_lib.aspe on camera nav_stereoPort with "/data/settings/lrm/vo_nearROI/"
EVS Port1 66/1/GNC_NISA_MGR 13: GNC NISA Manager Child Task: Stopped vo loop
EVS Port1 66/1/GNC_NISA_MGR 3: Processing an asp ack command after disabling VO.
EVS Port1 66/1/NISA 4: Some or all requested cameras or interfaces are already busy
EVS Port1 66/1/ASP 12: Engine #0: Receiving in bool: (1, 2264, 0, '\n\0\0\0')
EVS Port1 66/1/ASP 12: Engine #0: Ack got: 10
EVS Port1 66/1/ASP 12: Engine #0: Expecting: 10
EVS Port1 66/1/ASP 12: Engine #0: Success: Received an ack on disabling VO.
EVS Port1 66/1/NISA 11: Turning camera nav_stereoPort sensor OFF
EVS Port1 66/1/NISA 11: Sequence for camera nav_stereoPort finished
EVS Port1 66/1/NISA 11: Turning camera nav_stereoStarboard sensor OFF
EVS Port1 66/1/NISA 11: Sequence for camera nav_stereoStarboard finished
.EVS Port1 66/1/GNC_NISA_MGR 3: Processing an asp ack command, cc is: 11.

EVS Port1 66/1/GNC_NISA_MGR 2: GNC NISA Manager: OD Disabling
EVS Port1 66/1/GNC_NISA_MGR 2: GNC NISA Manager: Waiting for the process to send an ack.
EVS Port1 66/1/GNC_NISA_MGR 13: GNC NISA Manager Child Task: Stopped od loop. Note that the OD cam must now be rebooted
EVS Port1 66/1/GNC_NISA_MGR 3: Processing an asp ack command after disabling OD.
EVS Port1 66/1/ASP 12: Engine #0: Receiving in bool: (1, 2264, 0, '\v\0\0\0')
EVS Port1 66/1/ASP 12: Engine #0: Ack got: 11
EVS Port1 66/1/ASP 12: Engine #0: Expecting: 11
EVS Port1 66/1/ASP 12: Engine #0: Success: Disabling OD.
EVS Port1 66/1/ASP 12: Engine #0: Receiving in bool: (1, 2264, 0, '\f\0\0\0')
EVS Port1 66/1/ASP 12: Engine #0: Ack got: 12
EVS Port1 66/1/ASP 12: Engine #0: Expecting: 12
EVS Port1 66/1/ASP 12: Engine #0: Success: Stopping EKF.
.EVS Port1 66/1/CFE_SB 25: Pipe Overflow,MsgId 0x8f6,pipe SBN_2_66_Pipe,sender COMMS_APP.LANDER TASK
EVS Port1 66/1/CFE_SB 25: Pipe Overflow,MsgId 0x8e6,pipe SBN_2_66_Pipe,sender TOF_APP
.EVS Port1 66/1/NISA 11: Processing an asp ack command, cc is: 9.

EVS Port1 66/1/NISA 11: Starting sequence for camera nav_stereoStarboard, fcn 73
EVS Port1 66/1/NISA 11: Setting camera nav_stereoStarboard autoexposure settling time to 1.000000 s
EVS Port1 66/1/NISA 11: Setting camera nav_stereoStarboard autoexposure zone to 800,252:2568x2568
EVS Port1 66/1/NISA 11: Sending camera nav_stereoStarboard autoexposure controls to 0,0,0,0,20.000000 ms
EVS Port1 66/1/NISA 11: Sequence for camera nav_stereoStarboard finished
EVS Port1 66/1/ASP 12: Engine #0: Receiving in bool: (1, 2264, 0, '\t\0\0\0')
EVS Port1 66/1/ASP 12: Engine #0: Ack got: 9
EVS Port1 66/1/ASP 12: Engine #0: Expecting: 9
EVS Port1 66/1/ASP 12: Engine #0: Exception: 6
EVS Port1 66/1/ASP 12: Engine #0: Success: set autoexposure for camera mask 1
EVS Port1 66/1/ASP 12: Engine #0: Now sending a tlm msg about script status
EVS Port1 66/1/NISA 11: Processing an asp ack command, cc is: 10.

EVS Port1 66/1/NISA 11: Starting sequence for camera nav_stereoStarboard, fcn 74
EVS Port1 66/1/NISA 11: Turning camera nav_stereoStarboard autoexposure ON
EVS Port1 66/1/NISA 11: Turning camera nav_stereoStarboard sensor ON
EVS Port1 66/1/NISA 11: Setting camera nav_stereoStarboard frame to 800,252:2568x2568
EVS Port1 66/1/NISA 11: Setting camera nav_stereoStarboard subsampling to mode 1, factor 3
EVS Port1 66/1/NISA 11: Setting camera nav_stereoStarboard raw image save type to 100
EVS Port1 66/1/NISA 11: Using autoexposure for camera nav_stereoStarboard, settling for 1.000000 s
.EVS Port1 66/1/NISA 11: Capturing image from camera nav_stereoStarboard
EVS Port1 66/1/NISA 11: Turning camera nav_stereoStarboard sensor OFF
EVS Port1 66/1/NISA 11: Captured image sequence from camera nav_stereoStarboard with sequence ID 11804
EVS Port1 66/1/NISA 11: Compressing image from camera nav_stereoStarboard, quality 50
EVS Port1 66/1/NISA 11: Generated compressed image from camera nav_stereoStarboard with job ID 561
EVS Port1 66/1/NISA 11: Preparing to download 20496-byte image /data/postprocess/images/2025/1104/1902/CSYS-12590-20251104_190200_526925.jpg fro$
EVS Port1 66/1/NISA 11: Downloading image from camera nav_stereoStarboard to cf/nisa/images/nav/lrm_nav_stereoStarboard_2025-11-04T190200Z_J0000$
EVS Port1 66/1/NISA 11: Download of image from camera nav_stereoStarboard to /cf/nisa/images/nav/lrm_nav_stereoStarboard_2025-11-04T190200Z_J000$
EVS Port1 66/1/NISA 11: Sequence for camera nav_stereoStarboard finished
..EVS Port1 66/1/CFE_SB 25: Pipe Overflow,MsgId 0x880,pipe SBN_2_66_Pipe,sender COMMS_APP.COMMS_TO_TASK
EVS Port1 66/1/CFE_SB 25: Pipe Overflow,MsgId 0x8e6,pipe SBN_2_66_Pipe,sender TOF_APP
EVS Port1 66/1/CFE_SB 7: Duplicate Subscription,MsgId 0x8d8 on ASP_ENGINE00_PIPE pipe,app ASP
EVS Port1 66/1/CFE_SB 7: Duplicate Subscription,MsgId 0x808 on ASP_ENGINE00_PIPE pipe,app ASP
EVS Port1 66/1/CFE_SB 7: Duplicate Subscription,MsgId 0x8d8 on ASP_ENGINE00_PIPE pipe,app ASP
EVS Port1 66/1/CFE_SB 7: Duplicate Subscription,MsgId 0x808 on ASP_ENGINE00_PIPE pipe,app ASP
....EVS Port1 66/1/CFE_SB 25: Pipe Overflow,MsgId 0x8f6,pipe SBN_2_66_Pipe,sender COMMS_APP.LANDER TASK
EVS Port1 66/1/CFE_SB 25: Pipe Overflow,MsgId 0x8e6,pipe SBN_2_66_Pipe,sender TOF_APP
....................................................EVS Port1 66/1/SCH 18: Multiple slots processed: slot = 9, count = 4
.............#