failed
fm_app-testrunner
fm_app_tests.c - CallCount CFE_MSG_Init() (0)

fm_cmd_utils-testrunner

fm_dispatch-testrunner
71 failed, anything with fm_dispatch_tests or utstubs

fm_tbl-testrunner

fm_child-testrunner
5 failed out of 1057


[BEGIN] 76 Test_FM_ChildDirListPktCmd_PathAndEntryLengthGr
[ PASS] 76.001 fm_child_tests.c:1752 - FM_ChildDirListPktCmd(&queue_entry)
[ PASS] 76.002 fm_child_tests.c:59 - FM_GlobalData.ChildCmdCounter (1) == cmd_ctr (1)
[ PASS] 76.003 fm_child_tests.c:60 - FM_GlobalData.ChildCmdErrCounter (0) == cmderr_ctr (0)
[ FAIL] 76.004 fm_child_tests.c:61 - FM_GlobalData.ChildCmdWarnCounter (0) == cmdwarn_ctr (1)
[ PASS] 76.005 fm_child_tests.c:63 - FM_GlobalData.ChildPreviousCC (7) == previous_cc (7)
[ PASS] 76.006 fm_child_tests.c:64 - FM_GlobalData.ChildCurrentCC (0) == 0 (0)
[ PASS] 76.007 fm_child_tests.c:1757 - CallCount OS_DirectoryOpen() (1) == 1 (1)
[ PASS] 76.008 fm_child_tests.c:1758 - CallCount OS_DirectoryRead() (2) == 2 (2)
[ FAIL] 76.009 fm_child_tests.c:1759 - CallCount CFE_EVS_SendEvent() (1) == 2 (2)
[ PASS] 76.010 fm_child_tests.c:1760 - context_CFE_EVS_SendEvent[0].EventType (2) == CFE_EVS_EventType_INFORMATION (2)
[ FAIL] 76.011 fm_child_tests.c:1761 - context_CFE_EVS_SendEvent[0].EventID (72) == FM_GET_DIR_PKT_WARNING_EID (73)
[ PASS] 76.012 fm_child_tests.c:1764 - ReportPtr->FirstFile (0) == 0 (0)
[ PASS] 76.013 fm_child_tests.c:1765 - ReportPtr->TotalFiles (1) == 1 (1)
[ FAIL] 76.014 fm_child_tests.c:1766 - ReportPtr->PacketFiles (1) == 0 (0)
[  END] 76 Test_FM_ChildDirListPktCmd_PathAndEntryLengthGr TOTAL::14    PASS::10    FAIL::4     MIR::0     TSF::0     TTF::0     WARN::0


fm_cmds-testrunner

fm_ftp-testrunner




