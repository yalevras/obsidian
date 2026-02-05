




ci_lab_app.c

set_uplink_ctrl

- lets only 1 obc receive commands at a time
- we want to remove this

2 ways to receive, umbilical or read up link

- when we receive data, we need to have more error checking. make sure we are receiving a command not a telemetry packet
- in spacewire packet, make sure path check validity of wha we are receiving

155: address this comment

275: does this impact the set_uplink_ctrl or are we keeping it as just hkobc

312 & 345: do we need these comments

IN CI_LAB_ReadUpLink
![[Pasted image 20250922113442.png]]




So basically whats happening is we can get rid of the uplink control as the obc it is designated for is going to be either sent by wifi for hkobc or umbilical for pobc, the issue arises when you want to go through the dtn radio, but for that Roman’s ipn address node for each obc will go to that first and then it will get sent to the obcs so we do not need to worry about extra redundancy we do not need