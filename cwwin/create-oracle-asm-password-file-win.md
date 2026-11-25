## Create an Oracle ASM Password File

In certain situations, you must create an Oracle ASM password file before you can upgrade to Oracle Grid Infrastructure 19c.

On Windows platforms, if you are upgrading Oracle Grid Infrastructure from release 11.2.0.4 to release 12.1.0.2, and then upgrade to Oracle Grid Infrastructure 19c, you must create an Oracle ASM password file before starting the upgrade to Oracle Grid Infrastructure 19c.

However, if you upgrade from Oracle Grid Infrastructure 11.2.0.4 directly to Oracle Grid Infrastructure 19c, or if you upgrade from Oracle Grid Infrastructure 12.1.0.2 directly to Oracle Grid Infrastructure 19c, then this task is not required.

If you do not complete this task before starting the upgrade process, then you will get a failed check during installation. If you choose to ignore the error and continue the upgrade, then the `rootcrs` script fails to complete and generates the following error:

    2016-06-28 20:20:33: Command output:
       CLSRSC-661: The Oracle ASM password file does not exist at location
      C:\app\12.1.0\grid\database\PWD+ASM.ora.

After upgrading Oracle Grid Infrastructure from release 11.2.0.4 to release 12.1.0.2, complete the following steps to resolve this error before continuing with the upgrade to Oracle Grid Infrastructure 19c:

1.  Start the `ASMCMD` utility from the upgraded Oracle Grid Infrastructure home directory.
        Grid_home_12102\bin\asmcmd.bat
2.  Set the Oracle ASM disk group compatibility to 12.1.0.0.0 or higher for the disk group that stores the Oracle Cluster Registry (OCR).
        ASMCMD> setattr -G disk_group_name compatible.asm 12.1.0.0.0
3.  Create an Oracle ASM password file.
        ASMCMD> pwcreate --asm +disk_group_name/orapwASM sys_password
4.  Verify the password file was created.
        ASMCMD> pwget --asm
        +disk_group_name/orapwasm

**Parent topic:** [Preparing to Upgrade an Existing Oracle Clusterware Installation](preparing-to-upgrade-an-existing-oracle-clusterware-installation.md)
