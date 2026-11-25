## Oracle Grid Infrastructure Installation Server Hardware Checklist

Review server hardware requirements for Oracle Grid Infrastructure installation.

Table 1-1 Server Hardware Checklist for Oracle Grid Infrastructure

| Check                                                          | Task                                                                                                                                                                                                                                                                                                                      |
|:---------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Server Display Cards                                           | At least 1024 x 768 display resolution for Oracle Universal Installer. Confirm display monitor.                                                                                                                                                                                                                           |
| Minimum Random Access Memory (RAM)                             | At least 16 GB RAM for Oracle Grid Infrastructure installations, including installations where you plan to install Oracle RAC.                                                                                                                                                                                            |
| Virtual Memory configuration                                   | Oracle recommends that you set the paging file size to match the amount of RAM available on the server, up to a maximum of 16 GB                                                                                                                                                                                          |
| Intelligent Platform Management Interface (IPMI) Configuration | • IPMI cards installed and configured, with IPMI administrator account information available to the person running the installation.<br>• Ensure baseboard management controller (BMC) interfaces are configured, and have an administration account user name and password to provide when prompted during installation. |

**Related Topics**

- [Configuring Servers for Oracle Grid Infrastructure and Oracle RAC](configuring-servers-for-oracle-grid-infrastructure-and-oracle-rac.md)

**Parent topic:** [Oracle Grid Infrastructure Installation Checklist](oracle-grid-infrastructure-installation-checklist.md)
