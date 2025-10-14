Oct 3rd, 2025
I'm leaving early today at like 3:30.
Working on NSP unit tests as the MSI's don't seem to be working on both the EDU rover and the flatsat. The connection between the nisa and the illuminator board for the leds is faulty.


Oct 14th, 2025
The MSI script now works, I still have to push changes in the nisa.asp in messages for compression changes. I had to update both the compressed and raw scripts, both have not been committed. Now getting an error where when trying to command the camera to download images through ground, we are not getting them correctly. The first one after starting cfs_draco works the first time after a few tries, when switching sequence IDs it downloads the same one originally, maybe in the CSP packet it is not updating the info correctly. It could also be a memset issue in the cfs code?