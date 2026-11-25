Depending on the type of database installation and user account used as the Oracle Home User, Windows services run under low-privileged, non-administrative accounts such as a LocalService, or an authenticated Windows User Account, or as a high-privileged Local System Account (LSA) in Oracle home.

Table C-1 Running Windows Services

| Type of Installation                                                               | Oracle Home User     | Windows Service User for the Services                                                                                                                 |
|:-----------------------------------------------------------------------------------|:---------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------|
| Oracle Database Server                                                             | Windows User Account | Windows User Account                                                                                                                                  |
| Oracle Database Server                                                             | Built-in Account     | Local System Account                                                                                                                                  |
| Oracle Database Client                                                             | Windows User Account | Windows User Account                                                                                                                                  |
| Oracle Database Client                                                             | Built-in Account     | LocalService                                                                                                                                          |
| Oracle Grid Infrastructure (with the Grid Infrastructure Management Repository)    | Windows User Account | Grid Listeners using LocalService<br>Database services using Windows User Account<br><sup>Foot 1</sup>Clusterware services using Local System Account |
| Oracle Grid Infrastructure (without the Grid Infrastructure Management Repository) | Built-in Account     | Grid Listeners using LocalService<br>Clusterware services using Local System Account                                                                  |

<sup>Footnote 1</sup>

Clusterware requires administrative privileges so it always uses Local System Account to run Windows services.

**Parent topic:** [About Windows Services for Oracle Database](about-windows-services-for-oracle-database.md)
