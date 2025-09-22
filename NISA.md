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