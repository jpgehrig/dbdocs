## Fleet Patching and Provisioning Logs and Trace Files

Use Oracle Fleet Patching and Provisioning logs and traces to obtain more information for identifying and debugging Oracle FPP Server and client errors.

The following log and trace files are generated during Oracle FPP Server and client operations. These are the key log and trace files of interest for diagnostic purposes:

- `$ORACLE_BASE/crsdata/$HOSTNAME/rhp/rhpserver.log.{n}`

  Contains a detailed log of the actions that occur for the Oracle FPP Server operations. The log file numbers are updated automatically, and `.0` is always the most recent log file.

- `$ORACLE_BASE/crsdata/$HOSTNAME/rhp/srvmhelper_clsn_{unixtimestamp}.log.0`

  Contains a detailed log of the actions that occur during the Oracle FPP helper operations.

- `$ORACLE_BASE/crsdata/$HOSTNAME/rhp/logs/catalina.out`

  Contains a detailed log of the actions that occur during the Java Application Server operations.

- `/u01/app/grid/diag/crs/fpps/crs/trace`

  Contains a detailed log of the actions that occur during the Oracle Grid Infrastructure operations. Oracle Fleet Patching and Provisioning is part of the Oracle Grid Infrastructure stack and thus Cluster Ready Services daemon (CRSD) log and trace files can be useful to debug stop and start errors of the Oracle FPP Server or client.

- `$ORACLE_BASE/cfgtoollogs/dbca`

  Contains a detailed log of the actions that occur during the Oracle Database deployment.

- `$ORACLE_BASE/cfgtoollogs/dbua`

  Contains a detailed log of the actions that occur during the Oracle Database upgrade.

You can also use the Trace File Analyzer (TFA) to collect Oracle FPP logs and traces by using the `–rhp` flag. For example:

    $ tfactl diagcollect –rhp

**Parent topic:** [Fleet Patching and Provisioning Postinstallation Tasks](oracle-fpp-postinstallation-tasks.md)
