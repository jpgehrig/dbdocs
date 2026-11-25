## Daemon Control Command Reference

Use the `daemon` command to control the OMS daemon process.

### Syntax

    daemon exit
    trace lvl

### Usage Notes

The `exit` option marks the shared memory segment deleted and requests the daemon process to cleanly exit.

The `trace` option sets the verbosity of tracing to the daemon trace file. The verbosity levels are low, medium, and high. The default tracing verbosity is medium.

The daemon trace file is located at `$ORACLE BASE/diag/oms/$ORACLE SID oms *.trc`.

**Related Topics**

- [About the OMS Daemon](about-oms-daemon.md)

**Parent topic:** [Oracle Memory Speed CLI Commands](oms-cli-commands.md)
