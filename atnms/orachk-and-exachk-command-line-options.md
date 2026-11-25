Most command-line options apply to both Oracle ORAchk and Oracle EXAchk. Use the command options to control the behavior of Oracle ORAchk and Oracle EXAchk.

### Syntax

    $ ./orachk options

    [-h] [-a] [-b] [-v] [-p] [-m] [-u] [-f] [-o]
    [-clusternodes clusternames]
    [-failedchecks previous_result]
    [-nordbms]
    [-output path]
    [-dbnames dbnames]
    [-localonly]
    [-debug]
    [-dbnone | -dball]
    [-c]
    [-upgrade | -noupgrade]
    [-syslog]
    [-skip_usr_def_checks]
    [-checkfaileduploads]
    [-uploadfailed all | comma-delimited list of collections]
    [-fileattr [start | check | remove ] [-includedir path ] [-excludediscovery] [-baseline path [-fileattronly]
    [-testemail all | "NOTIFICATION_EMAIL=comma-delimited list of email addresses"]
    [-setdbupload all | db upload variable, for example, RAT_UPLOAD_CONNECT_STRING, RAT_UPLOAD_PASSWORD]
    [-unsetdbupload all | db upload variable, for example, RAT_UPLOAD_CONNECT_STRING, RAT_UPLOAD_PASSWORD]
    [-checkdbupload]
    [-getdbupload]
    [-cmupgrade]
    [-sendemail "NOTIFICATION_EMAIL=comma-delimited list of email addresses"]
    [-nopass]
    [-noscore]
    [-showpass]
    [-show_critical]
    [-diff Old Report New Report [-outfile Output HTML] [-force]]
    [-merge report 1 report 2 [-force]]
    [-tag tagname]
    [-nodaemon]
    [-profile asm | clusterware | corroborate | dba | ebs | emagent | emoms | em | goldengate | hardware | maa | oam | oim | oud | ovn | peoplesoft | preinstall | prepatch | security | siebel | solaris_cluster | storage | switch | sysadmin | timesten | user_defined_checks |  zfs ]
    [-excludeprofile asm | clusterware | corroborate | dba | ebs | emagent | emoms | em | goldengate | hardware | maa | oam | oim | oud | ovn | peoplesoft | preinstall | prepatch | security | siebel | solaris_cluster | storage | switch | sysadmin | timesten | user_defined_checks | zfs ]
    [-acchk -javahome path to jdk8
    -asmhome path to asm-all-5.0.3.jar -appjar directory where jar files are present for concrete class -apptrc directory where trace files are present for coverage class]
    [-check check ids | -excludecheck check ids]
    [-zfsnodes nodes]
    [-zfssa appliance names]
    [-dbserial | -dbparallel [n] | -dbparallelmax]
    [-idmpreinstall | -idmpostinstall | -idmruntime] [-topology topology.xml |
    -credconfig credconfig] | -idmdbpreinstall | -idmdbpostinstall | -idmdbruntime]
    [-idm_config IDMCONFIG] [-idmdiscargs IDMDISCARGS]
    [-idmhcargs IDMHCARGS | -h]

    $ ./exachk options

    [-h] [-a] [-b] [-v] [-p] [-m] [-u] [-f] [-o]
    [-clusternodes clusternames]
    [-output path]
    [-dbnames dbnames]
    [-localonly]
    [-debug]
    [-dbnone | -dball]
    [-c]
    [-upgrade | -noupgrade]
    [-syslog] [-skip_usr_def_checks]
    [-checkfaileduploads]
    [-uploadfailed all | comma-delimited list of collections]
    [-fileattr start | check | remove [-includedir path [-excludediscovery] [-baseline path[-fileattronly]
    [-testemail all | "NOTIFICATION_EMAIL=comma-delimited list of email addresses"]
    [-setdbupload all | db upload variable, for example, RAT_UPLOAD_CONNECT_STRING, RAT_UPLOAD_PASSWORD]
    [-unsetdbupload all | db upload variable, for example, RAT_UPLOAD_CONNECT_STRING, RAT_UPLOAD_PASSWORD]
    [-checkdbupload]
    [-getdbupload]
    [-cmupgrade] [-sendemail "NOTIFICATION_EMAIL=comma-delimited list of email addresses"]
    [-nopass]
    [-noscore]
    [-showpass]
    [-show_critical]
    [-diff Old Report New Report [-outfile Output HTML] [-force]]
    [-merge report 1 report 2 [-force]]
    [-tag tagname]
    [-auto_restart -initsetup | -initdebugsetup | -initrmsetup | -initcheck | -h]
    [-d start|start_debug|stop|status|info|stop_client|nextautorun|-h]
    [-nodaemon]
    [-unlockcells all | -cells comma-delimited list of names or IPs of cells] [-lockcells all | -cells comma-delimited list of names or IPs of cells]
    [-usecompute]
    [-exadiff Exalogic collection1 Exalogic collection2]
    [-vmguest ]
    [-hybrid [-phy nodes]]
    [-profile asm | bi_middleware | clusterware | compute_node | exatier1 | control_VM | corroborate | dba | ebs | el_extensive | el_lite | el_rackcompare | emagent | emoms | em | goldengate | hardware | maa | nimbula | obiee | ovn | peoplesoft | platinum | preinstall | prepatch | security | siebel | solaris_cluster | storage | switch | sysadmin | timesten | user_defined_checks | virtual_infra]
    [-excludeprofile asm | bi_middleware | clusterware | compute_node | exatier1 | control_VM | corroborate | dba | ebs | el_extensive | el_lite | el_rackcompare | emagent | emoms | em | goldengate | hardware | maa | nimbula | obiee | ovn | peoplesoft | platinum | preinstall | prepatch | security | siebel | solaris_cluster | storage | switch | sysadmin | timesten | user_defined_checks | virtual_infra]
    [-check check ids | -excludecheck check ids]
    [-cells cells]
    [-ibswitches switches]
    [-torswitches]
    [-extzfsnodes nodes]
    [-dbserial | -dbparallel [n] | -dbparallelmax | -allserial]
    [-allserial | -dbnodeserial |-cellserial | -switchserial]

- [Running Generic Oracle ORAchk and Oracle EXAchk Commands](generic-orachk-and-exachk-commands.md)
  List of command options common to Oracle ORAchk and Oracle EXAchk.
- [Controlling the Scope of Checks](controlling-scope-checks.md)
  Use the list of commands in this section to control the scope of checks.
- [Managing the Report Output](managing-report-output.md)
  Use the list of commands in this section to manage the report output.
- [Uploading Results to Database](uploading-results-database.md)
  Use the list of commands in this section to upload results to the database.
- [Configuring the Daemon Mode](configuring-daemon-mode.md)
  Use the daemon to configure automatic health check runs at scheduled intervals.
- [Controlling the Behavior of the Daemon](controlling-behavior-daemon.md)
  Use the list of commands in this section to control the behavior of the daemon.
- [Tracking File Attribute Changes](tracking-file-attribute-changes.md)
  Use the Oracle ORAchk and Oracle EXAchk `-fileattr` option and command flags to record and track file attribute settings, and compare snapshots.

**Parent topic:** [Appendixes](appendixes.md)
