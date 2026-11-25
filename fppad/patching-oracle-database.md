## Patching Oracle Database

To patch an Oracle database, you move the database home to a new home, which includes the patches you want to implement.

Use the `rhpctl move database` command to move one or more database homes to a working copy of the same database release level. The databases may be running on a working copy, or on an Oracle Database home that is not managed by Fleet Patching and Provisioning.

When the move operation is initiated by a Fleet Patching and Provisioning Server or Client, the version moved to must be a working copy of a gold image. You can also perform this operation using the independent automaton in an environment where no Fleet Patching and Provisioning Server is present. In this case, the source and destination homes are not working copies of gold images, but are two installed homes that you deployed with some method other than using Fleet Patching and Provisioning.

The working copy to which you are moving the database can be at a lower patch level than the current database home. This facilitates rollback in the event that you encounter any problems after moving to the higher level patched home.

The working copy to which you are moving the database home can be at the same patch level as the original working copy. This is useful if you are moving a database home from one storage location to another, or if you wish to convert an unmanaged home to a managed home while staying at the same patch level.

Fleet Patching and Provisioning applies all patches out-of-place, minimizing the downtime necessary for maintenance. Fleet Patching and Provisioning also preserves the current configuration, enabling the rollback capability previously described. By default, Fleet Patching and Provisioning applies patches in a rolling manner, which reduces, and in many cases eliminates, service downtime. Use the `-nonrolling` option to perform patching in non-rolling mode. The database is then completely stopped on the old `ORACLE_HOME`, and then restarted to make it run from the newly patched `ORACLE_HOME`.

**Note:**

Part of the patching process includes applying Datapatch. When you move an Oracle Database 12c release 1 (12.1) or higher, Fleet Patching and Provisioning completes this step for you. When you move to a version previous to Oracle Database 12c release 1 (12.1), however, you must run Datapatch manually. Fleet Patching and Provisioning is Oracle Data Guard-aware, and will not apply Datapatch to Oracle Data Guard standbys.

Workflow for Database Patching

Assume that a database named `myorcldb` is running on a working copy that was created from an Oracle Database 12c release 2 (12.2) gold image named `DB122`. The typical workflow for patching an Oracle Database home is as follows:

1.  Create a working copy of the Oracle Database that you want to patch, in this case `DB122`.
2.  Apply the patch to the working copy you created.
3.  Test and validate the patched working copy.
4.  Use the `rhpctl add image` command to create a gold image (for example, `DB122_PATCH`) from the patched working copy.
    **Note:**

    The working copy you specify in the preceding command must be hosted on the Fleet Patching and Provisioning Server in Fleet Patching and Provisioning-managed storage.
5.  Delete the patched working copy with the patched Oracle Database using the `rhpctl delete workingcopy` command.
    **Note:**

    Do not remove directly using the `rm` command or some other method, because this does not update the Fleet Patching and Provisioning inventory information.
6.  Create a working copy from the patched gold image, (`DB122_PATCH`).
7.  Move `myorcldb` to the working copy you just created.
8.  When you are confident that you will not need to roll back to the working copy on which the database was running at the beginning of the procedure, delete that working copy using the `rhpctl delete workingcopy` command.

Patching Oracle Database in a Data Guard Environment

Oracle Fleet Patching and Provisioning Server checks if the role of the database allows the execution of `datapatch` and acts accordingly. For example, if the database role is primary, Oracle FPP runs `datapatch` at the end of the moving process, and does not run `datapatch` if the database role is physical standby.

However, Oracle FPP is not aware of the standby topology and does not check for the patching level of the working copy on the standby locations. You must ensure that the standby database is always moved to a patched working copy before moving the primary database. Also, if you move the standby database to a patched working copy and a switchover or a failover occurs before moving the primary database to the patched working copy, it is possible that `datapatch` has not been executed on the primary database. This is because both sites have been moved to the patched working copy when the role was physical standby. In this case, you must run `datapatch` manually on the primary database.

Patching Oracle Database Using Batches

During database patching, Fleet Patching and Provisioning can sequentially process batches of nodes, with a number of nodes in each batch being restarted in parallel. This method maximizes service availability during the patching process. You can define the batches on the command line or choose to have Fleet Patching and Provisioning generate the list of batches based on its analysis of the database services running in the cluster.

Adaptive Oracle RAC-Rolling Patching for OJVM Deployments

In a clustered environment, the default approach for applying database maintenance with Fleet Patching and Provisioning is Oracle RAC rolling. However, non-rolling may be required if the new (patched) database home contains OJVM patches. In this case, Fleet Patching and Provisioning determines whether the rolling approach is possible, and rolls when applicable. (See MOS Note 2217053.1 for details.)

**Related Topics**

- [Patching Oracle Grid Infrastructure](patching-oracle-grid-infrastructure.md)
- [Provisioning Copies of Gold Images](provisioning-gold-image-copies.md)
- [Adding Gold Images to the Fleet Patching and Provisioning Server](adding-gold-images-to-oracle-fpp-server.md)
- [RHPCTL Command Reference](rhpctl-command-reference.md)

**Parent topic:** [Patching and Upgrading Oracle Database](patching-and-upgrading-oracle-database.md)
