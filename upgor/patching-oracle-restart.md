After you have upgraded to Oracle Grid Infrastructure for a standalone server (Oracle Restart) 19c, you can install individual software patches by downloading them from My Oracle Support.

1.  Download the patches that you want to apply from My Oracle Support:
    <https://support.oracle.com>

    Select the Patches and Updates tab to locate the patch.

    Oracle recommends that you select Recommended Patch Advisor, and enter the product group, release, and platform for your software.

    Place the patches in a shared directory that is accessible to all users.
2.  Review the README file for the patch that you want to apply, and complete all of the required steps before installing the patch.
3.  As the `root` user, go to the `/OPatch` directory in the Grid home.
        # cd /u01/app/grid/product/19.0.0/grid/OPatch
4.  Install the version of the OPatch utility that is recommended in the README file for the patch.
5.  Follow the instructions in the README file for the patch to apply the patch.
        # opatchauto apply patch_directory_location/patch_ID
6.  As the `grid` user, verify the release patch number for your Oracle Restart.
        $ Grid_home/bin/crsctl query has releasepatch

    The release patch number changes only for Release Update (RU) and Release Update Revision (RUR) patches.

**Parent topic:** [Upgrading and Patching Oracle Restart](upgrading-and-patching-oracle-restart.md)
