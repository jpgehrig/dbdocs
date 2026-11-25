## User Group Management in Fleet Patching and Provisioning

When you create a working copy of a gold image as part of a move or upgrade operation, Fleet Patching and Provisioning configures the operating system groups in the new working copy to match those of the source software home (either the unmanaged or the managed home from which you move or upgrade).

When you create a gold image of SOFTWARE image type, any user groups in the source are not inherited and images of this type never contain user group information. When you provision a working copy from a SOFTWARE gold image using the `rhpctl add workingcopy` command, you can, optionally, configure user groups in the working copy using the `-groups` parameter.

The `rhpctl move database`, `rhpctl move gihome`, `rhpctl upgrade database`, and `rhpctl upgrade gihome` commands all require you to specify a source home (either an unmanaged home or a managed home (working copy) that you provisioned using Fleet Patching and Provisioning), and a destination home (which must be a working copy).

When you have provisioned the destination home using the `rhpctl add workingcopy` command, prior to performing a move or upgrade operation, you must ensure that the groups configured in the source home match those in the destination home. Fleet Patching and Provisioning configures the groups as part of the add operation.

When you create a gold image of either the ORACLEGISOFTWARE or the ORACLEDBSOFTWARE image type from a source software home (using the `rhpctl import image` command) or from a working copy (using the `rhpctl add image` command), the gold image inherits the Oracle user groups that were configured in the source. You cannot override this feature.

You can define user groups for ORACLEGISOFTWARE and ORACLEDBSOFTWARE working copies using the `rhpctl add workingcopy` command, depending on the image type and user group, as discussed in the subsequent sections.

This section describes how Fleet Patching and Provisioning manages user group configuration, and how the `-groups` command-line option of `rhpctl add workingcopy` functions.

### ORACLEGISOFTWARE (Oracle Grid Infrastructure)

When you provision an Oracle Grid Infrastructure working copy of a gold image, the groups are set in the working copy according to the type of provisioning (whether regular provisioning or software only, and with or without the `-local` parameter), and whether you specify the `-groups` parameter with `rhpctl add workingcopy`. You can define OSDBA and OSASM user groups in Oracle Grid Infrastructure software with either the `-softwareonly` command parameter or by using a response file with the `rhpctl add workingcopy` command.

If you are provisioning only the Oracle Grid Infrastructure software using the `-softwareonly` command parameter, then you cannot use the `-groups` parameter, and Fleet Patching and Provisioning obtains OSDBA and OSASM user group information from the active Grid home.

If you use the `-local` command parameter (which is only valid when you use the `-softwareonly` command parameter) with `rhpctl add workingcopy`, then Fleet Patching and Provisioning takes the values of the groups from the command line (using the `-groups` parameter) or uses the default values, which Fleet Patching and Provisioning obtains from the `osdbagrp` binary of the gold image.

If none of the preceding applies, then Fleet Patching and Provisioning uses the installer default user group.

If you are provisioning and configuring a working copy using information from a response file, then Fleet Patching and Provisioning:

1.  Uses the value of the user group from the command line, if provided, for OSDBA or OSASM, or both.

2.  If you provide no value on the command line, then Fleet Patching and Provisioning retrieves the user group information defined in the response file.

If you are defining the OSOPER Oracle group, then, again, you can either use the `-softwareonly` command parameter or use a response file with the `rhpctl add workingcopy` command.

If you use the `-softwareonly` command parameter, then you can provide the value on the command line (using the `-groups` parameter) or leave the user group undefined.

If you are provisioning and configuring a working copy of a gold image using information from a response file, then you can provide the value on the command line, use the information contained in the response file, or leave the OSOPER Oracle group undefined.

### ORACLEDBSOFTWARE (Oracle Database)

If you are provisioning a working copy of Oracle Database software and you want to define Oracle groups, then use the `-groups` command parameter with the `rhpctl add workingcopy` command. Oracle groups available in the various Oracle Database releases are as follows:

- Oracle Database 11g release 2 (11.2)

  - OSDBA
  - OSOPER

- Oracle Database 12c release 1 (12.1)

  - OSDBA
  - OSOPER
  - OSBACKUP
  - OSDG
  - OSKM

- Oracle Database 12c release 2 (12.2) and later

  - OSDBA
  - OSOPER
  - OSBACKUP
  - OSDG
  - OSKM
  - OSRAC

Regardless of which of the preceding groups you are defining (except for OSOPER), Fleet Patching and Provisioning takes the values of the groups from the command line (using the `-groups` parameter) or uses the default values, which Fleet Patching and Provisioning obtains from the `osdbagrp` binary of the gold image.

If any group picked up from the `osdbagrp` binary is not in the list of groups to which the database user belongs (given by the `id` command), then Fleet Patching and Provisioning uses the installer default user group. Otherwise, the database user is the user running the `rhpctl add workingcopy` command.

**Parent topic:** [Provisioning Copies of Gold Images](provisioning-gold-image-copies.md)
