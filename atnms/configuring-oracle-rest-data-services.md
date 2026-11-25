- Configuring REST Using the Included ORDS
  Override default ORDS configuration by setting the shell environment variables.
- Configuring REST Using an Existing ORDS Installation

**Parent topic:** [Analyzing Risks and Complying with Best Practices](purpose-oracle-orachk-and-oracle-exachk.md)

### 2.11.1 Configuring REST Using the Included ORDS

Override default ORDS configuration by setting the shell environment variables.

- By default, Oracle REST Data Services (ORDS) uses whichever port is available in the range `7080`-`7085`. If no port in this range is available, then ORDS exits and prompts you to set the `RAT_ORDS_PORT` environment variable. If `RAT_ORDS_PORT` is already set, then ORDS uses the port specified in the `RAT_ORDS_PORT` environment variable.

- By default, ORDS is setup with the administrator user `ordsadmin`. You can override this by specifying a different user in the `RAT_ORDSADMIN_USER` environment variable.

- Depending on Oracle ORAchk and Oracle EXAchk, ORDS is started as a `nologin` user named either `ordsorachk` or `ordsexachk`. If you use the ORDS, which is already running, then the user is as same as who is running ORDS.

- If Oracle Trace File Analyzer is installed, then ORDS picks `JAVA_HOME` from `TFA_HOME`. If Oracle Trace File Analyzer is not installed, then ORDS picks the default `JAVA_HOME`. It is a requirement that you use JDK8. However, you can override by setting the `RAT_JAVAEXE` environment variable.

**Parent topic:** Configuring Oracle REST Data Services (ORDS)

### 2.11.2 Configuring REST Using an Existing ORDS Installation

1.  To add the `orachk.jar` file to the existing `ords.war` file:
        ./orachk -ordssetup ords_war_dir -configdir config_dir
        ./exachk -ordssetup ords_war_dir -configdir config_dir

    where,

    `ords_war_dir` is the directory that contains the `ords.war` file

    `config_dir` is an optional directory that you can specify to store the ORDS configuration files. If you do not specify the optional directory, then the configuration files are stored in the `orda_war_dir` directory.

    Stopping and restarting ORDS after running the `-ordssetup` command:
    - Adds the `orachk.jar` file to the existing `ords.war` file

    - Adds the user `ordsadmin` to the `ords.war` file, and grants `ORAchk admin` privileges to `ordsadmin`
2.  To start the Oracle ORAchk or Oracle EXAchk daemon:
        ./orachk -d start -ords ords_war_dir
        ./exachk -d start -ords ords_war_dir

After completion, open the `ords_war_dir``/log/ords_setup.log` file to view the REST URL details.

**Parent topic:** Configuring Oracle REST Data Services (ORDS)
