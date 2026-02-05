od (purple) must run before vo (green)

Rover Pausing:

PAUSE THINKING AREA

dist_this_segment__m = Vec3_DistToPoint(LOC_DrvTaskData.segment.start_pose.pos, current_pose.pos, Vec3_Scale(LOC_DrvTaskData.segment.translate_speed__mps_fwd, Quat_FwdAxis(LOC_DrvTaskData.segment.start_pose.rot)) );

// compute how many cells we've moved forward since the OD result was actually captured

//Add 0.5 to the result of the distance to point before casting to an integer to implement rounding to the nearest integer value

int8_t od_result_shift = (int)(0.5 + LOC_OD_CAM_TO_ROVER_FRONT_DIST + Vec3_DistToPoint(image_trigger_pose.pos, current_pose.pos, Quat_FwdAxis(current_pose.rot))/LOC_OD_MAP_RESOLUTION);

keep checking this

if od_result_shift > 6

pause the rover

poll for just an od result

else if the 11th cell is unknown

pause the rover

poll for a SUCCESSFUL od result

Some terms:

Pose:

ROI: region of interest

Bayer pattern:
![[Pasted image 20250922113212.png]]
Chromatic aberration:
![[Pasted image 20250922113222.png]]![[Pasted image 20250922113227.png]]
![[Pasted image 20250922113235.png]]




block diagram of faultry

if it never comes what happens

distance driven not time based

wait until things get updated so things that are yellow don’t get moved into my nimal region of 10 cells in the beginning

60 cm



![[Pasted image 20250922113342.png]]




THIS WORKS

bool LOC_DriveTask_CheckPauseConditions(void)

{

    OS_MutSemTake(LOC_SharedData.mutex);

    // could add this as a LOC_SharedData maybe should so we don't need to recompute

    //if (od_result_shift != 0){

    //printf("OD_RESULT_SHIFT: %d\n", od_result_shift);

    //}

    //if (LOC_DrvTaskData.OD_Map[10] != 0){

    //printf("OD_MAP: %d\n", LOC_DrvTaskData.OD_Map[10]);

    //}

    //if (LOC_SharedData.pause_flag != 0){

    //printf("PAUSE_FLAG: %d\n", LOC_SharedData.pause_flag);

    //}

    bool od_new = LOC_SharedData.od_new;

    bool donotexecute = 1;

  

    if (od_new){

        printf("!!!!! THERE IS A NEW OD RESULT !!!!!");

    }

    LOC_SharedData.od_new = false;

    //if (od_new)

    //{

        U_Pose image_trigger_pose = LOC_SharedData.od_image_trigger_pose[OD_IMG_TRIGGER_QUEUE_SIZE-1];

        U_Pose current_pose = LOC_SharedData.rover_pose;

        int8_t temp_shift = od_result_shift2;

        od_result_shift2 = (int)(0.5 + LOC_OD_CAM_TO_ROVER_FRONT_DIST + Vec3_DistToPoint(image_trigger_pose.pos, current_pose.pos, Quat_FwdAxis(current_pose.rot))/LOC_OD_MAP_RESOLUTION);

    //}

    if (od_result_shift2 != temp_shift){

        printf("!!!!!!!!!! CURRENT OD RESULT SHIFT: %d", od_result_shift2);

        }

    if (od_result_shift2 > 6) {

        printf("paused because od_result_shift > 6");

        LOC_SharedData.pause_flag = true;

    }

    else if (LOC_DrvTaskData.OD_Map[10] == LOC_OD_MAP_UNKNOWN && donotexecute == 0){

        // Notionally this works??

  

        printf("paused because about to enter path unknown");

        LOC_SharedData.pause_flag = true;

        /* Recenter the OD map on us */

        LOC_DriveTask_RecenterODMap();

  

        /* If there is a new OD output, modify list entries at the corresponding distances based on the safety estimates for roughness, slope, and coverage. */

        if (od_new)

        {

            printf("Updating OD map!!!!\n");

            LOC_Status update_status = LOC_DriveTask_UpdateOdMap(false, 0.0f);

            if (update_status != LOC_STATUS_OK)

            {

                printf("Something aint right chief\n");

                return false;

            }

        } /* End: if(od_new) */

    }

    else {

        LOC_SharedData.pause_flag = false;

    }

    OS_MutSemGive(LOC_SharedData.mutex);

}