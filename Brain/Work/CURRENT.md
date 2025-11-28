


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
rover pause:
		works but i think it needs more testing, i have not committed it yet
		clean up code
fm unit tests:
		fixing up nasa's mess?
nsp unit tests:
		 wip





SET VO_SET CORRENTLY IN THE SWITCH MODES FUNCTION
SET AUTORUN CORRECTLY IN NISA STATUS
IT IS RELYINc CURRENTLY ON THE 10 SECONDS WHICH IS WRONG!
UGHHAAAAAAAAA
ALSO DETERMINE WHEN IN THE NISA DOWNLOAD VO IMAGES IS IT TAKING A LOT OF TIME PUT SOME PRINTS AND STUFF







debug app: PULL REQUEST SUBMITTED
		clean up code done
		demonstrate for johnathan done
		default to debug done
		swap users without restarting app
			check if shell has already started and usernames are not the same 
		This is done!
to_lab messages: PULL REQUEST SUBMITTED
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
		This is done!

