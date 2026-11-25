Understand the options that you can supply to the Oracle Trace File Analyzer installer script to customize the installation.

Without parameters the Oracle Trace File Analyzer installation script will take you through an interview process for installation.

The Oracle Trace File Analyzer installation script appends `/tfa` to `-tfabase` if it is not already there.

The Oracle Trace File Analyzer installation script writes the log to the `/tmp/tfa_install_``timestamp``.log` file, for example, `/tmp/tfa_install_9263_2018_09_25-07_55_52.log`.

### Syntax

    installTFA-platform [[-local][-deferdiscovery][-tfabase install dir][-javahome path to JRE][-silent]|-extractto extract dir|-responsefile response file|-noorachk]

### Parameters

Table E-1 installTFA-\<platform\> Command Parameters

| Parameter         | Description                                                                                |
|:------------------|:-------------------------------------------------------------------------------------------|
| `-local`          | Installs only on the local node.                                                           |
| `-deferdiscovery` | Discovers Oracle trace directories after installation completes.                           |
| `-tfabase`        | Installs in the directory specified.                                                       |
| `-javahome`       | Use this directory for the JRE. Do not use this option along with the `-extractto` option. |
| `-silent`         | Use this option to not to ask any install questions.                                       |
| `-extractto`      | Extracts Oracle Trace File Analyzer into the directory specified (non-daemon mode).        |
| `-tmploc`         | Extracts the install archive into the temporary directory location specified (must exist). |
| `-debug`          | Displays debug tracing and does not remove `TFA_HOME` on install failure.                  |
| `-perlhome`       | Specify the custom location for Perl binaries.                                             |
| `-responsefile`   | Specify the response file to use to drive Oracle Trace File Analyzer setup parameters.     |
| `-noorachk`       | Specify the skip Oracle ORAchk autostart.                                                  |

**Parent topic:** [Oracle Trace File Analyzer Installer, Command-Line and Shell Options](tfa-command-reference.md)
