This procedure uses Fleet Patching and Provisioning to upgrade your Oracle Grid Infrastructure cluster from 11g release 2 (11.2.0.4) to 12c release 2 (12.2).

### Before You Begin

To upgrade to Oracle Grid Infrastructure 12c release 2 (12.2.0.1), your source must be Oracle Grid Infrastructure 11g release 2 (11.2.0.3 or 11.2.0.4), or Oracle Grid Infrastructure 12c release 2 (12.1.0.2).

Ensure that groups configured in the source home match those in the destination home.

Ensure that you have an image `GI_HOME_12201` of the Oracle Grid Infrastructure 12c release 2 (12.2.0.1) software to provision your working copy.

`GI_11204` is the active Grid Infrastructure home on the cluster being upgraded. It is a working copy because in this example, Fleet Patching and Provisioning provisioned the cluster. Fleet Patching and Provisioning can also upgrade clusters whose Grid Infrastructure homes are unmanaged that is, homes that Fleet Patching and Provisioning did not provision.

### Procedure

1.  Provision a working copy of the Oracle Grid Infrastructure 12c release 2 (12.2.0.1) software:
        $ rhpctl add workingcopy -workingcopy GI122 -image GI_HOME_12201 {authentication_option}

    `GI122` is the working copy based on the image `GI_HOME_12201`.
2.  Upgrade your target cluster to the `GI122` working copy:
        rhpctl upgrade gihome -sourcewc GI11204 -destwc GI122

    Rapid Home Provisioning identifies the cluster to upgrade based on the name of the source working copy, and upgrades to the working copy `GI122`.

**Parent topic:** [Fleet Patching and Provisioning Use Cases](fleet-patching-and-provisioning-use-cases.md)
