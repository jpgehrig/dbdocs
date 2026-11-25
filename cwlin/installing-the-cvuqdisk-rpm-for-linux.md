## Installing the cvuqdisk RPM for Linux

If you do not use an Oracle Database Preinstallation RPM, and you want to use the Cluster Verification Utility, then you must install the `cvuqdisk` RPM.

Without `cvuqdisk`, Cluster Verification Utility cannot discover shared disks, and you receive the error message "Package cvuqdisk not installed" when you run Cluster Verification Utility. Use the `cvuqdisk` RPM for your hardware (for example, `x86_64`).

1.  Locate the `cvuqdisk` RPM package, which is located in the directory Grid_home`/cv/rpm`. Where Grid_home is the Oracle Grid Infrastructure home directory.
2.  Copy the `cvuqdisk` package to each node on the cluster. You should ensure that each node is running the same version of Linux.
3.  Log in as `root`.
4.  Use the following command to find if you have an existing version of the `cvuqdisk` package:
        # rpm -qi cvuqdisk

    If you have an existing version of `cvuqdisk`, then enter the following command to deinstall the existing version:

        # rpm -e cvuqdisk
5.  Set the environment variable `CVUQDISK_GRP` to point to the group that owns `cvuqdisk`, typically `oinstall`. For example:
        # CVUQDISK_GRP=oinstall; export CVUQDISK_GRP
6.  In the directory where you have saved the `cvuqdisk` RPM, use the command `rpm -iv package` to install the `cvuqdisk` package. For example:
        # rpm -iv cvuqdisk-1.0.10-1.rpm

**Parent topic:** [Configuring Operating Systems for Oracle Grid Infrastructure on Linux](configuring-operating-systems-for-oracle-grid-infrastructure-on-linux.md)
