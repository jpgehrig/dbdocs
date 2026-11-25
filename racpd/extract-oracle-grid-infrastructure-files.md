## Extract the Oracle Grid Infrastructure Files

From your client connection to the Podman container as the `grid` user, download, extract Oracle Grid Infrastructure binaries, and the binary files to 19.16.

For example:

1.  Ensure that the Grid user has read-write-execute privileges in the software stage home in the Oracle RAC node 1 container (in this example,` /software/stage`).

2.  Confirm that you have downloaded and staged the required files for Oracle Grid Infrastructure and Oracle Database Release 19c (19.3), as well as the patch files. You must be able to see the Oracle Grid Infrastructure and Oracle Real Application Clusters (Oracle RAC) software staged under the path `/stage/software` inside the Oracle RAC Node 1 container.

        $ ls -l /software/stage/*.zip
        -rw-r--r--. 1 root 1001 3059705302 Feb 3 09:29 /software/stage/LINUX.X64_193000_db_home.zip
        -rw-r--r--. 1 root 1001 2889184573 Feb 3 09:30 /software/stage/LINUX.X64_193000_grid_home.zip
        -rw-r--r--. 1 root root 1006462657 Jul 29 20:36 /software/stage/p32869666_1916000ACFSRU_Linux-x86-64.zip
        -rw-r--r--. 1 root root 2814622872 Jul 28 09:13 /software/stage/p34130714_190000_Linux-x86-64.zip
        -rw-r--r--. 1 root root 275787541 Jul 28 19:52 /software/stage/p34339952_1916000OCWRU_Linux-x86-64.zip
        -rw-r--r--. 1 root 1001 124109254 Jun 3 01:46 /software/stage/p6880880_190000_Linux-x86-64.zip

3.  As the grid user, unzip the files at their intended location. For example:

        $ cd /u01/app/19c/grid
        $ unzip -q /software/stage/LINUX.X64_193000_grid_home.zip
        $ cd /software/stage
        $ unzip -q p34130714_190000_Linux-x86-64.zip
        $ unzip -q p34339952_1916000OCWRU_Linux-x86-64.zip
        $ unzip -q p32869666_1916000ACFSRU_Linux-x86-64.zip

4.  As the grid user, unzip the new OPatch version in the Oracle Grid Infrastructure home to replace the existing one. For example, where `OPATCH-patch-zip-file` is the OPatch zip file:

        $ cd /u01/app/19c/grid
        $ mv OPatch OPatch_19.3
        $ unzip -q /software/stage/OPATCH-patch-zip-file

    For example, for the OPatch 12.2.0.1.32 for DB 19.0.0.0.0 (Jul 2022) Product Oracle Global Lifecycle Management OPatch utility:

        $ cd /u01/app/19c/grid
        $ mv OPatch OPatch_19.3
        $ unzip -q /software/stage/p6880880_190000_Linux-x86-64.zip

After you unzip the OPatch zip file, you can remove the `OPatch_19.3` directory.

**Parent topic:** [Run the Oracle Grid Infrastructure Installer](run-oracle-grid-infrastructure-installer.md)
