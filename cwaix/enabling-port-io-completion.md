To ensure successful database, client, and grid infrastructure installation, set IOCP to `Available` using this procedure.

On IBM AIX on POWER Systems (64-bit), enable I/O completion ports (IOCP) to ensure successful database and grid infrastructure installation.

To check if the IOCP module is enabled, run the `lsdev` command:

    $ lsdev | grep iocp

The following sample output shows the IOCP status is set to `Defined` and hence not enabled:

    iocp0      Defined       I/O Completion Ports

By default, IOCP is set to `Defined`. To enable IOCP, set IOCP to `Available` using the following procedure:

1.  Log in as `root` and run the following command:
        # smitty iocp
2.  Select Change / Show Characteristics of I/O Completion Ports.
3.  Change configured state at system restart from Defined to `Available`.
4.  Run the `lsdev` command to confirm the IOCP status is set to `Available`:
        $ lsdev | grep iocp
        iocp0      Available       I/O Completion Ports

Restart the system to make the changes permanent.

**Parent topic:** [Configuring Operating Systems for Oracle Grid Infrastructure on IBM AIX on POWER Systems (64–Bit)](configuring-operating-systems-for-oracle-grid-infrastructure-on-ibm-aix-on-power-systems.md)
