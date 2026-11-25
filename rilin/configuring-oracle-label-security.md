## Configuring Oracle Label Security

After installation, you must configure Oracle Label Security in a database before you use it.

You can configure Oracle Label Security in two ways: with Oracle Internet Directory integration, or without Oracle Internet Directory integration.

Table 4-1 Options to Configure Oracle Label Security After Installation

| Configuration                                 | Requirement                                                                                                                                                                                                                                                                                                                                                                                                   |
|:----------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| With Oracle Internet Directory integration    | To configure Oracle Label Security with Oracle Internet Directory integration, Oracle Internet Directory must be installed in your environment and the Oracle database must be registered in the directory.                                                                                                                                                                                                   |
| Without Oracle Internet Directory integration | If you configure Oracle Label Security (OLS) without Oracle Internet Directory integration, then you cannot configure it to use Oracle Internet Directory at a later stage. To configure Oracle Label Security with Oracle Internet Directory on your database at a later time, you must remove the OLS option on the database, and then configure the OLS with Oracle Internet Directory integration option. |

**See Also:**

[Oracle Label Security Administrator's Guide](../olsag/oracle-label-security-using-oracle-internet-directory.md) for information about configuring Oracle Label Security

**Parent topic:** [Product-Specific Postinstallation Tasks](product-specific-postinstallation-tasks.md)
