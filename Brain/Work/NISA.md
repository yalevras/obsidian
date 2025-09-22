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

**Point clouds should be downloaded into a correct looking spot instead of getting put where they currently are**

- created /cf/pointcloud directory where StereoPointClouds are being stored, in gnc_nisa_mgr_task_od.c
    - File_CreateDir”(/cf/pointcloud”, 15); ← not sure if this should be done in nisa_app.c instead, or do a check to see if OD is enabled and then create the directory
- not sure how to actually download these pointclouds so I cannot verify this is working
- also not sure if this is the only place where pointclouds are saved

**Nisa asp acknowledgements are duplicated since the application is running on both OBC's, which means the scripts error out quite a bit.**

struct in app/asp/fsw/inc/…….

ack for each obc

add a field in the struct which states obc

try to only send acks when needed and if the camera is connected

edge cases:

one obc turns off or fails

one obc is on at once

both obcs are on

Changelog:

extern uint8_t tableMask;

extern uint8_t cameraStartedMask; both added in nisa_app.h

in HandleConfigTableLoad, if cameraInterfaceType == NISA_INTERFACE_TYPE_SERIAL

tableMask |= 1U << i; where i iterates between all of the cameras

once out of for loop

cameraStartMask = (tableMask & cameraMask);

Test plan:

Set mask in each case, 3 other cases

#define NISA_NOOP_CC 0                    no mask GOOD
#define NISA_RESET_COUNTERS_CC 1          no mask GOOD
#define NISA_INITIALIZE_CAMERAS_CC 2      no mask GOOD
#define NISA_PING_CAMERA_CC 5             mask    GOOD
#define NISA_SET_TIME_CC 6                mask    GOOD
#define NISA_QUERY_HEALTH_CC 7            mask    GOOD
#define NISA_QUERY_SPACE_CC 8             mask    GOOD
#define NISA_SET_AUTOEXPOSURE_CC 9        mask    GOOD
#define NISA_CAPTURE_IMAGE_CC 10          mask    GOOD
#define NISA_COMPRESS_IMAGE_CC 12         mask    GOOD
#define NISA_DOWNLOAD_IMAGE_CC 15         mask    GOOD
#define NISA_UPLOAD_FILE_CC 17            mask    GOOD
#define NISA_START_SCRIPT_CC 20           mask
#define NISA_PREPARE_SCRIPT_CC 21         mask
#define NISA_EXECUTE_SCRIPTS_CC 22        mask
#define NISA_RESET_SCRIPTS_CC 23          mask
#define NISA_STOP_SCRIPTS_CC 29           mask
#define NISA_REPLACE_APP_CC 30            mask    GOOD??? 
#define NISA_RAW_CAMERA_COMMAND_CC 60     mask    GOOD

![[Pasted image 20250922112100.png]]
![[Pasted image 20250922112114.png]]