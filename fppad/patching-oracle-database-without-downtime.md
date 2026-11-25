## Patching Oracle Database 19c Without Downtime

This procedure explains how to patch Oracle Database 19c with the latest patching without bringing down the database.

### Before You Begin

You have an Oracle Database `db19c` that you want to patch to the latest patch level.

Ensure that the working copy `db19c_psu` based on the image `DB19c_PSU` contains the latest patches and is available.

### Procedure

From the Fleet Patching and Provisioning Server, run one of the following commands as per your source and destination database:

1.  To patch an Oracle Database home managed by Fleet Patching and Provisioning, and there exist working copies of the source and destination databases, run:
        rhpctl move database -sourcewc db19c -patchedwc db19c_psu

    `db19c` is the source working copy of the database being patched

    `db19c_psu` is the working copy of the Oracle Database software with patches applied, based on the image `DB19c_PSU`.
2.  To patch an unmanaged Oracle Database home (source working copy does not exist because the Oracle home is not managed by Fleet Patching and Provisioning), run:
        rhpctl move database -sourcehome /u01/app/orabase/product/19.0.0/dbhome_1
         -patchedwc db19c_psu -targetnode node1

    `targetnode` specifies the node on which the database to be upgraded is running, because the source Oracle Database is on a 19c cluster.

    `/u01/app/orabase/product/19.0.0/dbhome_1` is the path of the database being patched

    `db19c_psu` is the working copy of the Oracle Database software with patches applied, based on the image `DB19c_PSU`.

    Use the saved gold image for standardized patching of all your databases of release 19c to the same patch level.
3.  If for some reason, you want to rollback the patches applied to a managed Oracle Database home, run:
        rhpctl move database -sourcewc db19c_psu
        -patchedwc db19c -ignorewcpatches

    `db19c` is the working copy of the unpatched database to which you want to roll back.

    `db19c_psu` is the working copy of the Oracle Database software with patches applied, based on the image `DB19c_PSU`.

For all Oracle Databases, you can also specify these additional options with the `move database` command:

- `-keepplacement`: For admin-managed Oracle RAC Databases (not Oracle RAC One Node Database), Fleet Patching and Provisioning retains the services on the same nodes after the move.

- `-disconnect`: Disconnects all sessions before stopping or relocating services.

- `-drain_timeout`: Specify the time, in seconds, allowed for resource draining to be completed for planned maintenance operations. During the draining period, all current client requests are processed, but new requests are not accepted. This option is available only with Oracle Database 12c release 2 (12.2) or later.

- `-stopoption`: Stops the database.

- `-nodatapatch`: Ensures `datapatch` is not run for databases you are moving.

Watch a video

**Parent topic:** [Oracle Fleet Patching and Provisioning Use Cases](fleet-patching-provisioning-use-cases.md)
