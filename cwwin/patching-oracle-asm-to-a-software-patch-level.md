## Patching Oracle ASM to a Software Patch Level

Starting with Oracle Grid Infrastructure 12c Release 1 (12.1), a new cluster state called Rolling Patch is available.

Rolling Patch mode is similar to the existing Rolling Upgrade mode in terms of the Oracle ASM operations allowed in this quiesce state.

1.  Download the patch you want to apply from My Oracle Support:
    1.  Go to [https://support.oracle.com](https://support.oracle.com/)
    2.  Select the Patches and Updates tab to locate the patch.
        To locate patch bundles, you can perform a Product or Family (Advanced) search for your platform and software release.

        Oracle recommends that you select Recommended Patch Advisor, and enter the product group, release, and platform for your software. My Oracle Support provides you with a list of the most recent patches and critical patch updates (CPUs).
    3.  Place the patch in an accessible directory, such as `C:\downloads`.
2.  Change directory to the `OPatch` directory in the Grid home.
    For example:

        C:\> cd C:\app\12.1.0\grid\opatch
3.  Review the patch documentation for the patch you want to apply, and complete all required steps before starting the patch upgrade.
4.  Follow the instructions in the patch documentation to apply the patch.

**Related Topics**

- [About Individual Oracle Grid Infrastructure Patches](about-individual-one-off-oracle-asm-patches.md)

**Parent topic:** [Applying Patches to Oracle Grid Infrastructure](applying-patches-to-oracle-grid-infrastructure.md)
