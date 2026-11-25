## General Guidelines for Operating System Packages

Review these guidelines before you proceed with installing operating system packages.

- Oracle recommends that you install Oracle Linux and use Oracle Database Preinstallation RPM to configure your operating systems for Oracle Database and Oracle Grid Infrastructure installations.

- The Oracle Database installation requires an X Window System (for example, `libX`). The `libX` packages are not part of a default Linux installation. If you perform an installation on a system with a reduced set of packages, then you must ensure that `libX` or a similar X Window System package is installed.

- The Unbreakable Enterprise Kernel for Oracle Linux can be installed on x86-64 servers running either Oracle Linux or Red Hat Enterprise Linux. As of Oracle Linux 5 Update 6, the Unbreakable Enterprise Kernel is the default system kernel. An x86 (32-bit) release of Oracle Linux including the Unbreakable Enterprise Kernel is available with Oracle Linux 5 update 7 and later.

- 32-bit packages in these requirements lists are needed only if you intend to use 32-bit client applications to access 64-bit servers that have the same operating system.

- Oracle Database 12c Release 2 (12.2) and later does not require the compiler packages `gcc` and `gcc-c++` on for Oracle Database or Oracle Grid Infrastructure installations.

- These operating system requirements do not apply to Oracle Engineered Systems, such as Oracle Exadata Database Machine. Oracle Engineered Systems include integrated system software that contain the required version of the operating system kernel and all software packages. Please verify that you have the minimum required Exadata image. Refer My Oracle Support note 888828.1 for more information.

**Related Topics**

- [My Oracle Support Note 888828.1](https://support.oracle.com/rs?type=doc&id=888828.1)

**Parent topic:** [Operating System Requirements for x86-64 Linux Platforms](operating-system-requirements-for-x86-64-linux-platforms.md)
