Use the `chactl query repository` command to view the maximum retention time, number of targets, and the size of the Oracle Cluster Health Advisor repository.

### Syntax

    chactl query repository [-help]

### Examples

To view information about the Oracle Cluster Health Advisor repository:

    $ chactl query repository
    specified max retention time(hrs) : 72
    available retention time(hrs)     : 212
    available number of entities      : 2
    allocated number of entities      : 0
    total repository size(gb)         : 2.00
    allocated repository size(gb)     : 0.07

**Parent topic:** [chactl Command Reference](chactl-command-reference.md)
