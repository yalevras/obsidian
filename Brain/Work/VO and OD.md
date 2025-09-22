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