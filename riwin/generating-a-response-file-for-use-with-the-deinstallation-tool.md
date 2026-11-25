## Generating a Response File For Use With the deinstall Command

To use a response file with the `deinstall` command, you must first create the response file.

You can generate the a response file by running the `deinstall.bat` command with the `-checkonly` and `-o` options before you run the command to deinstall the Oracle home, or you can use the response file template and manually edit it to create the response file.

Alternatively, you can use the response file template located at `%ORACLE_HOME%\deinstall\response\deinstall.rsp.tmpl`.

- To generate the response file `deinstall_dbhome_1.rsp` using the `deinstall.bat` command located in the Oracle home and the `-checkonly` option, enter a command similar to the following, where `C:\app\oracle\product\19.0.0\dbhome_1` is the location of the Oracle home and `C:\Users\oracle` is the directory in which the generated response file is created:
      C:\> app\oracle\product\19.0.0\dbhome_1\deinstall\deinstall.bat -checkonly -o C:\Users\oracle\

  For example, to use the response file with the `deinstall` command, run the following command:
      %ORACLE_HOME%\deinstall\deinstall.bat -paramfile response_file

**Parent topic:** [Using the Deinstallation Tool to Remove Oracle RAC](using-the-deinstallation-tool-to-remove-oracle-rac.md)
