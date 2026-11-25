## Oracle Home User Configurations for Oracle Installations

When the Oracle software installation completes, you will have one of the following configurations:

| Installation Type                                                                                  | Oracle Home user configuration                                                                                                                                                                                                                 |
|:---------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Oracle Grid Infrastructure with a domain user specified for the Oracle Home User                   | The Oracle Home user owns the Oracle Grid Infrastructure Management Repository service. The other services are run under the built-in Administrator account, except for the listeners, which run as LocalService (a built-in Windows account). |
| Oracle Grid Infrastructure with the Windows built-in Administrator account as the Oracle Home User | The Oracle Grid Infrastructure services are run under the built-in Administrator account, except for the listeners, which run as LocalService.                                                                                                 |
| Oracle RAC with specified Oracle Home User                                                         | The Oracle Home User owns all the services run by the Oracle Database software.                                                                                                                                                                |
| Oracle RAC with Built-in Oracle Home user                                                          | The services run under the built-in LocalSystem account.                                                                                                                                                                                       |

**Note:**

You cannot change the Oracle Home User after installation to a different Oracle Home User. Only out-of-place upgrade or move allows the Oracle Home User to be changed to or from the built-in Windows account.

**Parent topic:** [Creating Installation Groups and Users for Oracle Grid Infrastructure and Oracle RAC](creating-installation-groups-and-users-for-grid-and-rac.md)
