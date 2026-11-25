Use the `chactl set maxretention` command to set the maximum retention time for the diagnostic data.

The default and minimum retention time is 72 hours. If the Oracle Cluster Health Advisor repository does not have enough space, then the retention time is decreased for all the targets.

**Note:**

Oracle Cluster Health Advisor stops monitoring if the retention time is less than 24 hours.

### Syntax

    chactl set maxretention -time retention_time [-help]

Specify the retention time in hours.

### Examples

To set the maximum retention time to 80 hours:

    $ chactl set maxretention -time 80
    max retention successfully set to 80 hours

### Error Message

Error: `Specified time is smaller than the allowed minimum`

Description: This message is returned if the input value for maximum retention time is smaller than the minimum value.

**Parent topic:** [chactl Command Reference](chactl-command-reference.md)
