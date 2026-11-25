This procedure patches Oracle Grid Infrastructure and Oracle Databases on the cluster to the latest patch level without cluster downtime.

### Before You Begin

In this procedure, Oracle Grid Infrastructure 12c release 2 (12.2.0.1) is running on the target cluster. Working copy `GI_HOME_12201_WCPY` is the active Grid home on this cluster. Working copy `DB_HOME_12201_WCPY` runs an Oracle RAC 12c release 2 (12.2.0.1) Database with running database instance `db1`. Working copy `DB_HOME_12102_WCPY` runs an Oracle RAC 12c release 1 (12.1.0.2) Database with running database instance `db2`

Ensure that you have images `GI_HOME_12201_PSU1`, `DB_HOME_12201_PSU1`, `DB_HOME_12102_PSU5` with the required patches for Oracle Grid Infrastructure and Oracle RAC Database on the Fleet Patching and Provisioning Server.

The groups configured in the source home must match with those in the destination home.

### Procedure

1.  Prepare target Oracle homes as follows:
    1.  Provision software-only Grid home on the cluster to be patched:
            $ rhpctl add workingcopy -workingcopy GI_HOME_12201_PATCHED_WCPY
              -image GI_HOME_12201_PSU1 –client CLUSTER_005 -softwareonly
    2.  Provision each release Database home, without database instances, to be patched:
            $ rhpctl add workingcopy -workingcopy DB_HOME_12201_PATCHED_WCPY
              -image DB_HOME_12201_PSU1
            $ rhpctl add workingcopy -workingcopy DB_HOME_12102_PATCHED_WCPY
              -image DB_HOME_12102_PSU5
2.  Patch Oracle Grid Infrastructure and all Oracle RAC Databases on `node1` as follows:
        $ rhpctl move gihome -sourcewc GI_HOME_12201_WCPY -destwc GI_HOME_12201_PATCHED_WCPY -auto
          -dbhomes DB_HOME_12102_WCPY=DB_HOME_12102_PATCHED_WCPY,DB_HOME_12201_WCPY=DB_HOME_12201_PATCHED_WCPY  -targetnode node1 {authentication_option}

    When you run the command, you move your active Oracle Grid Infrastructure from working copy `GI_HOME_12201_WCPY` to `GI_HOME_12201_PATCHED_WCPY`, Oracle RAC Database `db1` from `DB_HOME_12201_WCPY` to `DB_HOME_12201_PATCHED_WCPY`, and Oracle RAC Database `db2` from `DB_HOME_12102_WCPY` to `DB_HOME_12102_PATCHED_WCPY`.

**Parent topic:** [Fleet Patching and Provisioning Use Cases](fleet-patching-and-provisioning-use-cases.md)
