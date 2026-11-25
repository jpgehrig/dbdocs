## Configuring Oracle ASM Disk Groups Manually using Oracle ASMCA

After installing Oracle Grid Infrastructure for a standalone server, you can also use Oracle ASMCA to create and configure disk groups, Oracle ADVM, and Oracle ACFS.

During Oracle Grid Infrastructure for a standalone server installation, Oracle Automatic Storage Management Configuration Assistant (Oracle ASMCA) utility creates a new Oracle Automatic Storage Management instance if there is no Oracle ASM instance currently configured on the computer. After installation, you can create and configure additional disk groups, and you can configure Oracle ADVM and Oracle ACFS.

To create disk groups or manually configure Oracle ASM disks, start Oracle ASMCA, where Grid_home is the path to the Oracle Grid Infrastructure home:

    $ cd Grid_home/bin
    $ ./asmca

**Related Topics**

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/manage-asm-asmca.md)

**Parent topic:** [Installing and Configuring Oracle Grid Infrastructure for a Standalone Server](installing-and-configuring-oracle-grid-infrastructure-for-a-standalone-server.md)
