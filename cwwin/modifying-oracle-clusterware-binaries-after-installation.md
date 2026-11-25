## Modifying Oracle Clusterware Binaries After Installation

After installation, if you must modify the software installed in your Grid home, then you must first stop the Oracle Clusterware stack.

For example, to apply a one-off patch, or modify any of the dynamic-link libraries (DLLs) used by Oracle Clusterware or Oracle ASM, you must follow these steps to stop and restart Oracle Clusterware.

**Caution:**

To put the changes you make to the Oracle Grid Infrastructure home into effect, you must shut down all executable files that run in the Grid home directory and then restart them. In addition, shut down any applications that use Oracle shared libraries or DLL files in the Grid home.

1.  Log in using a member of the Administrators group and go to the directory `Grid_home``\bin`, where Grid_home is the path to the Oracle Grid Infrastructure home.
2.  Shut down Oracle Clusterware using the following command:
        C:\..\bin> crsctl stop crs -f
3.  After Oracle Clusterware is completely shut down, perform the updates to the software installed in the Grid home.
4.  Use the following command to restart Oracle Clusterware:
        C:\..\bin> crsctl start crs
5.  Repeat steps 1 through 4 on each cluster member node.

**Note:**

Do not delete directories in the Grid home. For example, do not delete the directory `Grid_home``/OPatch`. If you delete the directory, then the Grid infrastructure installation owner cannot use Opatch to patch the Grid home, and Opatch displays the error message "`checkdir error: cannot create ``Grid_home``/OPatch`".

**Parent topic:** [Oracle Grid Infrastructure Postinstallation Tasks](oracle-grid-infrastructure-postinstallation-tasks.md)
