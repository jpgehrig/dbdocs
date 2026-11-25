## About the OMS Daemon

OMS is a user-space file system. The OMS daemon handles management and CLI operations for OMS.

You should run the OMS daemon at start up. At start up, the OMS daemon creates a shared memory segment for the exclusive use of OMS. There is one daemon per instance. Set the instance identifier (SID) before you start the OMS daemon.

Start the OMS daemon by running the `$ORACLE_HOME/bin/oms_daemon`.

    $ whoami
    oracle
    $ export ORACLE_SID="test"
    $ $ORACLE_HOME/bin/oms_daemon
    Starting daemon as a detached background.
    OMS binary located at /mnt/data/ssd0/obase/test/bin/oms_daemon
    OMS daemon startup: oms_test successfully created
    OMS daemon creating tracefile
    /mnt/data/ssd0/obase/diag/oms/test_oms_20758.trc
    $ ipcs
    ------ Message Queues --------
    key msqid owner perms used-bytes messages
    ------ Shared Memory Segments --------
    key shmid owner perms bytes nattch status
    0x00000000 32047104 oracle 640 135266304 1
    $ ls -l $ORACLE_HOME/dbs/*.ora
    -rwx------ 1 oracle dba 93 Feb 23 20:10
    /mnt/data/ssd0/oracle/test/dbs/oms_test.ora

In this example, the daemon creates a shared memory segment with shared memory id 32047104. It also creates a configuration file `$ORACLE_HOME/dbs/oms_test.ora`.

Oracle recommends that you should not delete the shared segment manually. Similarly, you should not edit or delete the configuration file. If you accidentally kill the daemon, you can restart it by running the command `$ORACLE_HOME/bin/oms_daemon`.

Daemon traces are available in the `$ORACLE_BASE/diag/oms` directory.

**Related Topics**

- [Daemon Control Command Reference](oms-daemon-control.md)

**Parent topic:** [Setting-Up the Oracle Memory Speed File System](setting-up-oms-filesystem.md)
