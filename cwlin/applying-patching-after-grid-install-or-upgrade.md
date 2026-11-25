## Applying Patches After an Oracle Grid Infrastructure Installation or Upgrade

You can apply patches to Oracle Grid Infrastructure deployment in rolling mode after a successful or a failed upgrade. This mode is similar to the "Rolling Upgrade" mode in terms of the Oracle ASM operations allowed in this quiesce state.

1.  Download patches you want to apply from My Oracle Support:
    <https://support.oracle.com>
    Select the Patches and Updates tab to locate the patch.

    Oracle recommends that you select Recommended Patch Advisor, and enter the product group, release, and platform for your software. My Oracle Support provides you with a list of the most recent Release Updates (RUs) and Release Update Revisions (RURs).

    Place the patches in an accessible directory, such as `/tmp`.
2.  Review the patch documentation for the patch you want to apply, and complete all required steps before starting the patch upgrade.
3.  Follow the instructions in the patch documentation to apply the patch on the first node.
        # Grid_home/OPatch/opatchauto apply patch_directory_location/patch_ID

    Wait for the patching to finish on the first node before patching other cluster nodes.
4.  Apply the patch on all other cluster nodes, one at a time.
        # Grid_home/OPatch/opatchauto apply patch_directory_location/patch_ID

**Related Topics**

- [OPatch User's Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/cwlin&id=OPTCH-GUID-D2E384A2-8881-4FD8-812D-C0F26B6EC41C)

**Parent topic:** [Patching Oracle Grid Infrastructure](patching-oracle-grid-infrastructure.md)
