To use AutoUpgrade to complete the upgrade, you first create a configuration file with AutoUpgrade from the new release Oracle home.

In the following example, the AutoUpgrade utility is run using the parameter `sample_config_file`. This parameter generates a configuration file in the home of the user running AutoUpgrade that you can edit to provide environment paths and settings and upgrade preferences for the upgrade. To generate the configuration file (`config`), you run AutoUpgrade from the new release Oracle Database home using the `sample_config_file` parameter, and specify an output file name.

**Note:**

AutoUpgrade is regularly updated. For additional examples, and for information about the most recent AutoUpgrade releases, including new command-line parameters and options, and new or enhanced configuration file parameters, refer to the Oracle Database Upgrade Guide for the release to which you want to upgrade. Also refer to the My Oracle Support note "AutoUpgrade Tool (Doc ID 2485457.1)," which will contain information about the most recent AutoUpgrade updates.

In this example, user `oracle` navigates to the location of an earlier release Oracle home, which in this example is Oracle Database 19c:

    cd /u01/app/oracle/product/19.0.0/

Next, the Oracle user starts AutoUpgrade from the Oracle Database 23c Oracle home, and creates a configuration file in its user home directory, `/home/oracle`:

    java -jar /u01/app/oracle/product/23/rdbms/admin/autoupgrade.jar -create_sample_file config
    Created sample configuration file /home/oracle/sample_config.cfg

After you create the configuration file, open it up in your preferred text editor, and modify parameter settings as needed for your environment.

    cd /
    vi sample_config.cfg

**Related Topics**

- [Oracle Database Documentation](https://docs.oracle.com/en/database/oracle/oracle-database/index.html)
- [AutoUpgrade Tool (Doc ID 2485457.1)](https://support.oracle.com/rs?type=doc&id=2485457.1)

**Parent topic:** [Preparing to Upgrade Oracle Database](preparing-to-upgrade.md)
