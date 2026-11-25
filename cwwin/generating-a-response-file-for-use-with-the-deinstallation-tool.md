## Generating a Response File For Use With the deinstall Command

To use a response file with the `deinstall` command, you must first create the response file.

You can generate the a response file by running the `deinstall.bat` command with the `-checkonly` and `-o` options before you run the command to deinstall the Oracle home, or you can use the response file template and manually edit it to create the response file.

Alternatively, you can use the response file template located at `%ORACLE_HOME%\deinstall\response\deinstall.rsp.tmpl`.

- To generate the response file `deinstall_OraCrs19c_home1.rsp` using the `deinstall.bat` command located in the Oracle home and the `-checkonly` option, enter a command similar to the following, where `C:\app\19.0.0\grid` is the location of the Grid home and `C:\Users\oracle` is the directory in which the generated response file is created:
      C:\> app\19.0.0\grid\deinstall\deinstall.bat -checkonly -o C:\Users\oracle\

**Parent topic:** [Using the deinstall Command to Remove Oracle Clusterware and Oracle ASM](using-the-deinstallation-tool-to-remove-oracle-clusterware-and-oracle-asm.md)
