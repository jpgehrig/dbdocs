## Restrictions and Guidelines for Oracle Home Users

Review the following restrictions and guidelines for Oracle Home Users for Oracle software installations.

- If you intend to use multiple Oracle Home Users for different Oracle Database homes, then Oracle recommends that you create a separate Oracle Home User for Oracle Grid Infrastructure software (Oracle Clusterware and Oracle ASM).

- If you plan to install Oracle Database or Oracle RAC, then Oracle recommends that you create separate Oracle Home Users for the Oracle Grid Infrastructure and the Oracle Database installations. If you use one Oracle Home User, then when you want to perform administration tasks, you must select the utilities from the Oracle home for the instance you want to administer, or change the default `%ORACLE_HOME%` value to the location of the Oracle Home from which the instance runs. For Oracle ASM instances, you must use the Oracle Grid Infrastructure home and for database instance use the Oracle Database home.

- If you try to administer an Oracle home or Grid home instance using `sqlplus`, `srvctl`, `lsnrctl`, or `asmcmd` commands while the environment variable `%ORACLE_HOME%` is set to a different Oracle home or Grid home path, then you encounter errors. For example, when you start SRVCTL from a database home, `%ORACLE_HOME%` should be set to that database home, or SRVCTL fails. The exception is when you are using SRVCTL in the Oracle Grid Infrastructure home. In that case, SRVTCL ignores `%ORACLE_HOME%`, and the Oracle home environment variable does not affect SRVCTL commands. In all other cases, you must start the utilities from the Oracle home of the instance that you want to administer.

  If you need to set the user environment to use a specific Oracle home, then use Oracle Universal Installer. On the landing page, click Installed Products. In the Inventory window, click the Environment tab. Select the Oracle Home you want to use, and deselect the other Oracle homes, then click Apply. You can then exit Oracle Universal Installer. When you use Oracle Universal Installer to set the Oracle Home, it updates the `ORACLE_HOME` environment variable and updates the `PATH` variable.

**Parent topic:** [When to Create an Oracle Home User](when-to-create-an-oracle-home-user.md)
