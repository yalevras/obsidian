GUI stuff:
	now working on exposure time from us to ms
	importPackage(org.csstudio.opibuilder.scriptUtil);
	
	var selection_widget = display.getWidget("CurrLanderCmd_LHANS").setValue("Connect");
active mode:
			dev: 49
			branch: feature/active-mode-vo
			committed and pushed: 11-20 11:00 am
		scripts:
			active_mode_setup_misst.asp -> works, unstable
			active_mode_setup_lrm.asp -> untested
			active_mode_drive_misst.asp -> partially works
			active_mode_drive_lrm.asp -> untested
			active_mode_stop_misst.asp -> works, stable
			active_mode_stop_lrm.asp -> untested
			vo_reset_new_drive.asp -> runs, unsure if works properly?
		when testing on lrm, need to upload vo_reset_new_drive.aspe
		fuck misst for now let's just do the edu
		cleanup code
		ask josh for power consumption for each device on the edu
		try smaller gaps between commands on asp
		
		CHANGES:
			cfs
			yamcs excel
			asp
			messages in asp
	funny port pano is having some issues!!!!!
	in dmesg on pobc
		usb 1-1.2: new high-speed USB device number 3 using musb-hdrc
		rndis_host 1-1.2:1.0: RNDIS init failed, -71
		rndis_host: probe of 1-1.2:1.0 failed with error -71
		cdc_acm 1-1.2:1.2: ttyACM0: USB ACM device
	also in /data/upload there is NOTHING????? did it get wiped is the harness just ass i do not know?????
	inside SS there is 
	capture_img_autoexposure.aspe
	liblrm-vo-wrapper.so
	liblrm_vo.so
	star_vo.aspe
	vo_close.aspe
	vo_init.aspe
	vo_reload_lib.aspe
	vo_reset_new_drive.aspe
	
	I PUT THREE OF THESE ON PORT PANO GET RID OF THEM I NEED PORT STEREO IM JUST STUPID
	
	SET VO_SET CORRENTLY IN THE SWITCH MODES FUNCTION
	SET AUTORUN CORRECTLY IN NISA STATUS
	IT IS RELYINc CURRENTLY ON THE 10 SECONDS WHICH IS WRONG!
	UGHHAAAAAAAAA
	ALSO DETERMINE WHEN IN THE NISA DOWNLOAD VO IMAGES IS IT TAKING A LOT OF TIME PUT SOME PRINTS AND STUFF
rover pause:
		works but i think it needs more testing, i have not committed it yet
		clean up code
fm unit tests:
		fixing up nasa's mess?
nsp unit tests:
		 wip
debug app: PULL REQUEST SUBMITTED
		clean up code done
		demonstrate for johnathan done
		default to debug done
		swap users without restarting app
			check if shell has already started and usernames are not the same 
		This is done!
to_lab messages: FIX
			dev: 49
			branch: feature/to_lab_messages
		what i know:
			hkobc sends messages through wifi
			pobc sends messages through umbilical
			currently both obcs subscribe to the same things, so if a table is loaded in both, something that the hkobc is supposed to send through wifi
		initial questions:
			how do i know
		other info:
			kiss encoding, keep it simple, stupid, protocol for emitting through radio or something
			ProcId 1 = HKOBC
			ProcId 2 = POBC

![[Pasted image 20251209141923.png]]
batch imaging: PULL REQUEST SUBMITTED
	- index for filelists
	i have figured out where it is just taking index one

		fileMsg->data.statusByRef.index = commStack->nl.hton_u32(1)
		add a value in NISA_ReferenceParameters_t