## AutoUpgrade Utility Configuration Files Parameters and Options

AutoUpgrade configuration files contain all the information required to perform Oracle Database upgrades.

Before you can use an AutoUpgrade processing mode, you must create an AutoUpgrade configuration file for the databases that you want to upgrade.

AutoUpgrade configuration files contain **global** and **local** configuration parameters. Global parameters by default apply to all databases addressed by the configuration file. When specified for a specific database, local configuration parameters override global parameters specified by the configuration file.

- [Locally Modifiable Global Parameters for AutoUpgrade Configuration File](locally-modify-global-parameters-autoupgrade-config-file.md)
  Required configuration parameters for AutoUpgrade can be set either globally for all upgrades, or locally.
- [Local Parameters for the AutoUpgrade Configuration File](local-parameters-autoupgrade-config-file.md)
  To configure information for specific Oracle Databases for the AutoUpgrade utility upgrade, you provide information in the AutoUpgrade local parameters.
- [Global Parameters for the AutoUpgrade User Configuration File](global-parameters-autoupgrade-config-file.md)
  To specify a default behavior for a parameter for all Oracle Database upgrades addressed in the configuration file, you can use the optional AutoUpgrade global parameters.

**Parent topic:** [Using AutoUpgrade for Oracle Database Upgrades](using-autoupgrade-oracle-database-upgrades.md)
