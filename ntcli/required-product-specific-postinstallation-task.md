## Configuring Oracle Net Services

You can configure Oracle Database Client to communicate with Oracle Net Services by adding the appropriate entries to the tnsnames.ora and listener.ora files.

If you have a previous release or Oracle software, you can just copy information in the Oracle Net tnsnames.ora and listener.ora configuration files from the previous release to the corresponding files in the new release.

**Note:**

The default location for the` tnsnames.ora` and `listener.ora` files is the `ORACLE_HOME``\network\admin `directory.

To create Oracle Connection Manager (CMAN) services, create a CMAN alias entry in `cman.ora` under `ORACLE_HOME``\network\admin`. For example:

`cman_proxy=`

` (CONFIGURATION=`

` (ADDRESS=(PROTOCOL=tcp)(HOST=``host_name``)(PORT=1521))`

` (RULE_LIST=`

` (RULE=(SRC=*)(DST=*)(SRV=*)(ACT=accept)))`

` (PARAMETER_LIST=`

` (MIN_GATEWAY_PROCESSSES=1)`

` (MAX_GATEWAY_PROCESSES=2)))`

This accepts connection from all clients as mentioned in the rule.

CMAN services are created when CMAN is started for the first time using `cmctl` command-line tool. When creating services, `cmctl` prompts for a password if Windows User Account is specified as Oracle Home User during installation. If Windows Built-in Account is specified as Oracle Home User during installation, then `cmctl` does not prompt for password.

Listener can be configured by adding an alias entry in `listener.ora.` Listener service is created when the listener is started for the first time. The listener control utility, `lsnrctl` prompts for a password if Windows User Account is specified as Oracle Home User during installation. If Windows Built-in Account is specified as Oracle Home User during installation, then it does not prompt for password.

**Parent topic:** [Required Postinstallation Tasks](required-postinstallation-tasks.md)
