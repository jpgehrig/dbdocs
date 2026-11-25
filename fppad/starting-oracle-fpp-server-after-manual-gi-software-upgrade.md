## Starting Oracle FPP Server After Manually Upgrading Oracle Grid Infrastructure

If you upgrade Oracle Grid Infrastructure manually, without using Oracle Fleet Patching and Provisioning (Oracle FPP) self upgrade feature, then Oracle FPP Server does not start after the upgrade.

When you manually upgrade Oracle Grid Infrastructure, the file system resources are disabled and that does not allow the Oracle FPP Server to start. When file system resources are disabled, you may get an error while starting the Oracle FPP Server. To resolve this error, you must first enable the file system and then start the Oracle FPP server.

1.  Enable file system on all the volumes and the storage disk groups.
        # srvctl enable filesystem -volume volume_name -diskgroup diskgroup_name
2.  Enable the volume and the disk group on which you enabled the file system.
        # srvctl enable volume -volume volume_name -diskgroup diskgroup_name
3.  Start the Oracle FPP Server.
        $ srvctl start rhpserver

**Parent topic:** [Upgrading Oracle Fleet Patching and Provisioning Server](upgrading-oracle-fpp-server.md)
