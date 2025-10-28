Oct 3rd, 2025
I'm leaving early today at like 3:30.
Working on NSP unit tests as the MSI's don't seem to be working on both the EDU rover and the flatsat. The connection between the nisa and the illuminator board for the leds is faulty.


Oct 14th, 2025
The MSI script now works, I still have to push changes in the nisa.asp in messages for compression changes. I had to update both the compressed and raw scripts, both have not been committed. Now getting an error where when trying to command the camera to download images through ground, we are not getting them correctly. The first one after starting cfs_draco works the first time after a few tries, when switching sequence IDs it downloads the same one originally, maybe in the CSP packet it is not updating the info correctly. It could also be a memset issue in the cfs code?

Oct 15th, 2025
Compression changes pushed.
MSI script still works, talk to Allen in the morning about the download issue on the MSI because it is acting very weird. Also flatsat having several issues, sbn not really working, constant disconnects between the OBCs. When running my script the flatsat is taking forever and the script is taking 7x longer to run.

Run someone elses cfs and see if ur still getting the sbn issue

Run my entire script from yamcs and see if i am still getting long wait times

Oct 16th, 2025

having two yamcs open was making the flatsat all laggy

fix button on gui
add nisa table to load button on gui and fix in js script

then join Allen in debugging nisa app

Oct 16th
To Do:
- try running download image off of POBC
- push gui changes



push gui changes

figure out asp in two directories in why its not working
write instruction manual for msi scripts



![[Pasted image 20251017160738.png]]




Oct 20th
Pull GUI changes to verify
Get setup on 56

did those

i started on debug changes
i am trying to figure out how to change the user we run the shell with instead of being root but another user so we cannot run certain commands. i also want to get a table with commands we shouldn't be allowed to run

we should run debug through es_start_app




look a little into jenkins




Oct 28th
okay so the script and command are working for nisa boot interrupt a little bit for now, BUT it is not sending the raw command on asp correctly i am getting malformed function call at nisa.asp:107:12