Use the `chactl resize repository` command to resize the tablespace of the Oracle Cluster Health Advisor repository based on the current retention time and the number of targets.

**Note:**

The `chactl resize repository` command fails if your system does not have enough free disk space or if the tablespace contains data beyond requested resize value.

### Syntax

    chactl resize repository -entities total number of hosts and database instances [-force | -eval] [-help]

### Examples

To set the number of targets in the tablespace to 32:

    chactl resize repository -entities 32
    repository successfully resized for 32 targets

**Parent topic:** [chactl Command Reference](chactl-command-reference.md)
