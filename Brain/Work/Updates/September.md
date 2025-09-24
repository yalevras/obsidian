Sept. 22nd
helped ishan with some debugging
my ci_lab stuff is NOT the issue with my asp script stuff there is something wrong with my compression parameters, i probably don't need to finalize this yet because the edu is not going to be ready to run msi stuff for a bit
to do:
- charge rover and pack it up tomorrow
	- checklist:
		- rover (strap to car)
		- black box
		- glass panel installation
		- MOXA route
		- 49->56
		- charge rover
		- mouse
		- keyboard
		- NUC power cable
- rover pause (probably do this wednesday once misst is more open and mitchell is in stratford)
- msi compression script, msi download script
- nsp unit tests

Sept. 23rd
helped mitchell debug a bunch, helped ishan debug stuff with the transfer from 49->56, then helped mitchell pack up the rover, went through the whole checklist and now moving on to doing stuff on 56
to do:
- rover pause -> wednesday
- msi compression script, msi download script
- nsp unit tests

Sept. 24th
morning: nsp unit tests (DONE), familiarize with rover pause (DONE), msi compression script
afternoon: try out rover pause in lab
- IT WORKS I CAN SEE HOW LONG WE HAVE DRIVEN SINCE THE LAST OD CYCLE WHICH IS SO GOOD
- next steps are to:
	- try to delay od and make it detect longer
		- DONE
	- speed up how fast we are going to induce things
		- slowed down and still works
- rover pausing works for distance now, i want to show Johnathan next and talk about the yellow field at the beginning. currently i have a condition in the rover pausing to not look at the other condition right now. curious if they work together
- ok last thing i did was try to do a final change i think the pause flag was not being set back after a new od result was detected so i added that but when i tried it out i got an invalid ekf out flag error so i'm going to try again tomorrow

Sept. 25th
