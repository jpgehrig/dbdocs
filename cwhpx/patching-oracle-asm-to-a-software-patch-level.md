Starting with Oracle Grid Infrastructure 12c Release 1 (12.1), a new cluster state, called Rolling Patch, is available. This mode is similar to the existing "Rolling Upgrade" mode in terms of the Oracle ASM operations allowed in this quiesce state.

1.  Download patches you want to apply from My Oracle Support:

    <https://support.oracle.com>

    Select the Patches and Updates tab to locate the patch.

    Oracle recommends that you select Recommended Patch Advisor, and enter the product group, release, and platform for your software. My Oracle Support provides you with a list of the most recent patch set updates (PSUs) and critical patch updates (CPUs).

    Place the patches in an accessible directory, such as `/tmp`.

2.  Change directory to the `/OPatch` directory in the Grid home. For example:

        $ cd /u01/app/19.0.0/grid/OPatch

3.  Review the patch documentation for the patch you want to apply, and complete all required steps before starting the patch upgrade.

4.  Follow the instructions in the patch documentation to apply the patch. For example:

        # ./opatch apply patch directory_location/patch_ID

**Parent topic:** [Applying Patches to Oracle Grid Infrastructure](applying-patches-to-oracle-asm.md)
