The microprocessors for the SPARC M7 and T7 series servers include Data Analytics Accelerator (DAX) coprocessors. These coprocessors perform query-related operations directly through the hardware, which improves Oracle Database performance.

Starting with Oracle Database 12c Release 2 (12.2) and later releases, the DAX feature is enabled by default for Oracle Database on Oracle Solaris on SPARC (64-Bit) systems. The `dax_access` privilege is available by default to the Oracle database installation owner (`oracle`) and all other users and processes as part of the basic Oracle Solaris operating system privilege set.

To use the DAX hardware with Oracle Database, you must install Oracle Database 12c Enterprise Edition, and enable the In–Memory option for your application.

For information about configuring the Oracle Database 12c in-memory feature, see Oracle Database In-Memory Guide.

**Note:**

The DAX feature is not supported for use with Kernel Zones at this time.

**Related Topics**

- [Oracle Database In-Memory Guide](../inmem/enabling-the-im-column-store.md)

**Parent topic:** [Recommended Postinstallation Tasks](recommended-postinstallation-tasks.md)
