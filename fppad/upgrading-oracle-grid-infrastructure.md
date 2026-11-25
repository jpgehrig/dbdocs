## Upgrading Oracle Grid Infrastructure

If you are using Fleet Patching and Provisioning, then you can use a single command to upgrade an Oracle Grid Infrastructure home.

Fleet Patching and Provisioning supports upgrades to Oracle Grid Infrastructure 19c from 11g release 2 (11.2.0.4), 12c release 1 (12.1.0.2), 12c release 2 (12.2), and 18c. The destination for the upgrade can be a working copy of a gold image already provisioned or you can choose to create the working copy as part of this operation.

As an example, assume that a target cluster is running Oracle Grid Infrastructure on an Oracle Grid Infrastructure home that was provisioned by Fleet Patching and Provisioning. This Oracle Grid Infrastructure home is 12c release 2 (12.2.0.1) and the working copy is named accordingly.

After provisioning a working copy version of Oracle Grid Infrastructure 19c (named GIOH12201 in this example), you can upgrade to that working copy with this single command:

    $ rhpctl upgrade gihome -sourcewc GIOH12201 -destwc GIOH19C

Fleet Patching and Provisioning is able to identify the cluster to upgrade based on the name of the source working copy. If the target cluster was running on an unmanaged Oracle Grid Infrastructure home, then you would specify the path of the source home rather than providing a source working copy name, and you must also specify the target cluster.

**Note:**

You can delete the source working copy at any time after completing an upgrade. Once you delete the working copy, however, you cannot perform a rollback. Also, use the `rhpctl delete workingcopy` command (as opposed to `rm`, for example) to remove the source working copy to keep the Fleet Patching and Provisioning inventory correct.

**Parent topic:** [Patching and Upgrading Oracle Grid Infrastructure](patching-and-upgrading-oracle-grid-infrastructure.md)
