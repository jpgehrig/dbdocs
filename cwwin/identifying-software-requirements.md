## Identifying Software Requirements

Depending on the products that you intend to install, verify that the required operating system software is installed on each node of your cluster.

Requirements listed in this document are current as of the date listed on the title page. To obtain the most current information about operating system requirements, see the online version in the Oracle Help Center at the following URL:

[https://docs.oracle.com/en/database/](../../../..)

OUI performs checks on your system to verify that it meets the listed operating system requirements. To ensure that these checks complete successfully, verify the requirements before you start OUI.

**Note:**

Oracle does not support running different operating system versions on cluster members, unless an operating system is being upgraded. You cannot run different operating system version binaries on members of the same cluster, even if each operating system is supported.

Table 3-1 Oracle Grid Software Requirements for Windows Systems

| Requirement         | Value                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:--------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| System Architecture | Processor: AMD64, or Intel Extended Memory (EM64T)<br>Note: Oracle provides only x64 releases of Oracle Database with Oracle RAC for Windows.<br>The x64 release of Oracle RAC runs on the x64 version of Windows on AMD64 and EM64T hardware.                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| Operating System    | Oracle Grid Infrastructure and Oracle RAC for x64 Windows:<br>• Windows Server 2025 x64 - Standard, Datacenter, and Essentials editions<br>• Windows Server 2022 x64 - Standard, Datacenter, and Essentials editions (Supported starting Oracle Database 19c Release Update 19.13 or later)<br>• Windows Server 2019 x64 - Standard, Datacenter, and Essentials editions<br>• Windows Server 2016 x64 - Standard, Datacenter, and Essentials editions<br>• Windows Server 2012 R2 x64 - Standard, Datacenter, Essentials, and Foundation editions<br>Note: Windows Multilingual User Interface Pack is supported. The Server Core option is not supported.                                 |
| Compiler and SDK    | The following component is supported only with Microsoft Visual C++ 2013 Update 5:<br>• Pro\*C/C++: Use Microsoft Visual C++ 2013 to convert the Pro\*C/C++ files into C/C++ files, and then use Microsoft Visual C++ 2017 Update 6 Version 15.6.3 or later to further build them.<br>The following components are supported with the compilers based on Microsoft Visual C++ 2017 Update 6 or later and Intel C++ 17.0 Update 8, and Microsoft Visual C++ 2017 Update 6 or later SDK:<br>• Oracle Call Interface (OCI)<br>• External callouts<br>• Oracle XML Developer's Kit (XDK)<br>• Oracle C++ Call Interface (OCCI)<br>Pro\*COBOL supports:<br>• Micro Focus Visual COBOL Version 6 |

**Related Topics**

- [Oracle Database Administrator’s Reference for Microsoft Windows](../ntqrf/overview-of-database-migration-from-a-32-bit-windows-computer.md)

**Parent topic:** [Configuring Operating Systems for Oracle Grid Infrastructure and Oracle RAC](configuring-operating-systems-for-oracle-grid-infrastructure-and-oracle-rac.md)
