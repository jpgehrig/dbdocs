## Upgrading to Oracle Grid Infrastructure 19c

This procedure uses Fleet Patching and Provisioning to upgrade your Oracle Grid Infrastructure cluster from 18c to 19c.

### Before You Begin

To upgrade to Oracle Grid Infrastructure 19c, your source must be Oracle Grid Infrastructure 11g release 2 (11.2.0.4), Oracle Grid Infrastructure 12c release 2 (12.1.0.2 or 12.2.0.1), or Oracle Grid Infrastructure 18c.

Ensure that groups configured in the source home match those in the destination home.

Ensure that you have an image `GI_HOME_19c` of the Oracle Grid Infrastructure 19c software to provision your working copy.

`GI_18c` is the active Grid Infrastructure home on the cluster being upgraded. It is a working copy because in this example, Fleet Patching and Provisioning provisioned the cluster. Fleet Patching and Provisioning can also upgrade clusters whose Grid Infrastructure homes are unmanaged that is, homes that Fleet Patching and Provisioning did not provision.

### Procedure

1.  Provision a working copy of the Oracle Grid Infrastructure 19c software:
        $ rhpctl add workingcopy -workingcopy GI9c -image GI_HOME_19c {authentication_option}

    `GI19c` is the working copy based on the image `GI_HOME_19c`.
2.  Upgrade your target cluster to the `GI19c` working copy:
        rhpctl upgrade gihome -sourcewc GI18c -destwc GI19c

    Rapid Home Provisioning identifies the cluster to upgrade based on the name of the source working copy, and upgrades to the working copy `GI19c`.

**Parent topic:** [Oracle Fleet Patching and Provisioning Use Cases](fleet-patching-provisioning-use-cases.md)
