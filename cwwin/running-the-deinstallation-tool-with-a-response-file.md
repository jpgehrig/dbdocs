## Running the deinstall command with a Response File

When running the `deinstall` command, you can use a response file instead of responding to each prompt individually.

The `deinstall` command uses the information you provide, plus information gathered from the software home to create a response file. You can alternatively supply a response file generated previously by the `deinstall.bat` command using the `–checkonly` option and `-o` option. You can also edit a response file template located at `Oracle_Home``\deinstall\response\deinstall.rsp.tmpl` to create a response file.

- To run the `deinstall.bat` command located in an Oracle Grid Infrastructure home and use a response file located at `D:\Users\oracle\paramfile4.tmpl`, enter the following commands while logged in as a member of the Administrators group:
      C:\> cd %ORACLE_HOME%
      C:\..grid> deinstall\deinstall.bat -paramfile D:\Users\oracle\paramfile4.tmpl

**Parent topic:** [Using the deinstall Command to Remove Oracle Clusterware and Oracle ASM](using-the-deinstallation-tool-to-remove-oracle-clusterware-and-oracle-asm.md)
