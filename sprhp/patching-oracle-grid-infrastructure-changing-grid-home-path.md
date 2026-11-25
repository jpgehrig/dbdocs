This procedure explains how to patch Oracle Grid Infrastructure without changing the Grid home path.

### Before You Begin

- Ensure that the gold image containing the Grid home is imported and exists on the Fleet Patching and Provisioning Server.

- Ensure that the directory you provide in the `­path` option is not an existing directory.

- The source Grid home must be a managed home (provisioned by Fleet Patching and Provisioning). It does not need to be an Oracle Layered File System (OLFS)-compliant home.

- The Grid home must be Oracle Grid Infrastructure 12c (12.2.0.1) or later.

### Procedure for Patching

- To move a non-OLFS-compliant Grid home to an OLFS Grid home, from the Fleet Patching and Provisioning Server, run two commands similar to the following:
      $ rhpctl add workingcopy -workingcopy GI_HOME_12201_PSU1 -aupath
        /u01/app/orabase/product/12.2.0.1/aupath -image image_name
        -client client_name -softwareonly

      $ rhpctl move gihome -srcwc GI_HOME_12201 -destwc GI_HOME_12201_PSU1 -agpath
        /u01/app/orabase/product/12.2.0.1/agpath -path
        /u01/app/orabase/product/12.2.0.1/grid
- To move an OLFS-compliant Grid home to a patched version, run two commands similar to the following:
      $ rhpctl add workingcopy -workingcopy gihome12201_psu1_lpm -aupath
        /u01/app/orabase/product/12.2.0.1/aupath -image image_name -client
        client_name -softwareonly

      $ rhpctl move gihome -sourcewc gihome12201_lpm -destwc gihome12201_psu1_lpm

**Parent topic:** [Fleet Patching and Provisioning Use Cases](fleet-patching-and-provisioning-use-cases.md)
