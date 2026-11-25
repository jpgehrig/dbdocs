These topics contain last-minute features and changes for Oracle Database 19c.

- Unsupported Products for the IBM AIX on POWER Systems Platform
- Linking Applications with Oracle Client Libraries for the IBM AIX on POWER Systems Platform
- Preinstallation Requirements for the IBM AIX on POWER Systems Platform
- Installation, Configuration, and Upgrade Issues for the IBM AIX on POWER Systems Platform
- Open Bugs Affecting the IBM AIX on POWER Systems Platform

### Unsupported Products for the IBM AIX on POWER Systems Platform

There are no unsupported products for the IBM AIX on POWER Systems Platform at this time. Refer to the list of unavailable products or features for all platforms in Oracle Database 19c.

**Parent topic:** Issues Affecting the IBM AIX on POWER Systems Platform for Oracle Database 19c

### Linking Applications with Oracle Client Libraries for the IBM AIX on POWER Systems Platform

You must use the dynamic Oracle client libraries to link the client code on Linux. Do not link the static Oracle client libraries.

**Parent topic:** Issues Affecting the IBM AIX on POWER Systems Platform for Oracle Database 19c

### Preinstallation Requirements for the IBM AIX on POWER Systems Platform

Refer to the installation guides for the preinstallation requirements for Oracle Database 19c.

**Parent topic:** Issues Affecting the IBM AIX on POWER Systems Platform for Oracle Database 19c

### Installation, Configuration, and Upgrade Issues for the IBM AIX on POWER Systems Platform

These topics describe information about issues that affect Oracle Database installation, configuration, and upgrade.

- Bug 29053538
- Bug 29434250
- Bug 29052788
- Bug 29178036

**Parent topic:** Issues Affecting the IBM AIX on POWER Systems Platform for Oracle Database 19c

#### Bug 29053538

Oracle database instance at startup loads `libora_netlib.so`. This library has dependencies on IBM XL Fortran runtime libraries. If they are not installed on the system, startup fails with the following error:

    ORA-40238: invalid linear algebra shared library

Workaround:

Install XL Fortran Runtime for AIX Fix Pack 10 (February 2018 PTF) for 15.1.

Download and install XL Fortran Runtime for AIX Fix Pack 10 (February 2018 PTF) for 15.1 from:

[https://www-01.ibm.com/support/docview.wss?uid=swg24044611](https://support.microsoft.com/en-in/help/3179560/update-for-visual-c-2013-and-visual-c-redistributable-package)

**Parent topic:** Installation, Configuration, and Upgrade Issues for the IBM AIX on POWER Systems Platform

#### Bug 29434250

If you install Oracle Database 19c or Oracle Grid Infrastructure 19c or upgrade Oracle Database 19c or Oracle Grid Infrastructure 19c from previous versions to 19c by registering with Enterprise Manager Cloud Control (EMCC), installer may crash.

Workaround:

Do not register with EMCC during install or upgrade. Instead, discover the host and add targets either using EMCC web console or Enterprise Manager Command Line Interface (EMCLI) commands after the install and upgrade is complete.

**Parent topic:** Installation, Configuration, and Upgrade Issues for the IBM AIX on POWER Systems Platform

#### Bug 29052788

In some environments, every time the Dynamic Host Configuration Protocol (DHCP) lease is renewed, a different IP address is assigned. The Cross-Doman Protocol (CDP) daemon does not see these changes, and assumes the IP address has not changed unless the CDP resource is restarted. Example, when the SCAN is stopped.  When the IP address changes, there is a window when CDP is unreachable by that IP, and the agent eventually executes a clean action and restarts.

Workaround:

If CDP is found to be offline when the SCAN VIP's IP changes, then use `srvctl start cdp` to restart it.

**Parent topic:** Installation, Configuration, and Upgrade Issues for the IBM AIX on POWER Systems Platform

#### Bug 29178036

The shutdown abort of Oracle RAC One Node Database software on IBM AIX on Power Systems 7.1 does not finish quickly and results in failing to failover.

Workaround:

IBM AIX on Power Systems 8 or later, and AIX 7.2 use hardware compression for Active Memory Expansion (AME) and therefore can support the use of 64k pages with AME. On AIX 7.1 or earlier, 64k pages are not supported when AME is enabled, and 4k pages are used instead. In certain scenarios when using 4k pages with the Oracle Database, certain operations may be slower, including startup and shutdown of the database. Use of AME with the Oracle RAC One Node Database software is not recommended unless using AIX 8 or later and AIX 7.2 or later with 64k pages enabled.

**Parent topic:** Installation, Configuration, and Upgrade Issues for the IBM AIX on POWER Systems Platform

### Open Bugs Affecting the IBM AIX on POWER Systems Platform

These topics contain last-minute features and changes for Oracle Database 19c.

**Parent topic:** Issues Affecting the IBM AIX on POWER Systems Platform for Oracle Database 19c
