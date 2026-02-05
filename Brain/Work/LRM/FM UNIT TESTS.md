failed
fm_app-testrunner
PASS 98

fm_cmd_utils-testrunner
PASS 182

fm_dispatch-testrunner
PASS 108

fm_tbl-testrunner
PASS 46

fm_child-testrunner
PASS 1062

fm_cmds-testrunner
PASS 234

fm_ftp-testrunner
still have to do this







UT_FM_Child_Cmd_Asset(1, 0, 0, queue_entry.CommandCode);

void UT_FM_Child_Cmd_Assert(int32 cmd_ctr, int32 cmderr_ctr, int32 cmdwarn_ctr, int32 previous_cc)

{

    UtAssert_INT32_EQ(FM_GlobalData.ChildCmdCounter, cmd_ctr);

    UtAssert_INT32_EQ(FM_GlobalData.ChildCmdErrCounter, cmderr_ctr);

    UtAssert_INT32_EQ(FM_GlobalData.ChildCmdWarnCounter, cmdwarn_ctr);

  

    UtAssert_INT32_EQ(FM_GlobalData.ChildPreviousCC, previous_cc);

    UtAssert_INT32_EQ(FM_GlobalData.ChildCurrentCC, 0);

}