![[Pasted image 20250922111903.png]]

Can see camera indexes for camera bit mask in cfs_draco/apps/nisa/fsw/tables

**cFS nisa application things to fix:**

**Nisa camera busy flags not reset on reload tables**

Every time reload table is called, within ProcessRequest in nisa_app.c, status is CFE_TBL_INFO_UPDATED, with which HandleConfigTableLoad() is called. When iterating through cameras to shut them down, a line is added to UnlockCameras which resets the busy flag to false.

**Nisa camera high exposure times not working**

Max exposure seems to be 1599ms, if the timeout on NISA_Transact in sequence-captureImage.c when turning the camera sensor off is set to 1000.

If increased to 2000, max exposure is increased to 2599ms.

If increased to 5000, max exposure is increased to 5599ms.

Etc.

![[Pasted image 20250922111925.png]]
![[Pasted image 20250922111931.png]]
![[Pasted image 20250922111939.png]]

When testing with misst, set time camera mask is 35, for star stereo, port stereo, and port pano.

When testing with flatsat, use nisa_config-lrm-failedPOBC.c, mask is 32 for port pano

**Nisa camera download file by name doesn’t work (need the id)**

We can send a name and it is being received properly as a file name into cameraTaskData→workingReference.spec.fileName

Ref type 0 = name

Ref type 1 = sequence_id

Ref type 2 = job_id

FIX: On YAMCS and CFS side change struct that is sent in through YAMCS to have a parameter for ID and download, and the only one that is used is the one that is needed through the refType parameter. Struct that was changes was NISA_ReferenceParameters_tT

![[Pasted image 20250922111959.png]]
![[Pasted image 20250922112007.png]]
This is what the id is supposed to look like
![[Pasted image 20250922112024.png]]
![[Pasted image 20250922112029.png]]