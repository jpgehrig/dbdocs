These topics contain last-minute features and changes for Linux for Oracle Database 19c.

- Certification Information
  The latest certification information for Oracle Database 19c is available in My Oracle Support note 1304727.2:
- Unsupported Products for Linux
  This topic describes products or features that are unavailable for Oracle Database 19c.
- Product Support
  This topic describes the supported products or features for Oracle Database 19c.
- Linking Applications with Oracle Client Libraries for Linux
  You must use the dynamic Oracle client libraries to link the client code on Linux. 
- Preinstallation Requirements for the Linux Platform
  Refer to the installation guides for the preinstallation requirements for Oracle Database 19c.
- Open Bugs Affecting Linux
  This topic contains last-minute features and changes for Oracle Database 19c.
- Known Issues and Bugs for SUSE Linux Enterprise Server 15
  This section contains information about issues related to SUSE Linux Enterprise Server 15:
- Unsupported Products for Oracle Database 19c on Oracle Linux 8
  The following products or features are unavailable for Oracle Database 19c on Oracle Linux 8.
- Known Issues and Bugs for Oracle Linux 8 and Red Hat Enterprise Linux 8
  This section contains information about issues related to Oracle Linux 8 and Red Hat Enterprise Linux 8:
- Installing Oracle Database 19c on Oracle Linux 8 and Red Hat Enterprise Linux 8
  To install Oracle Database 19c on Oracle Linux 8 or Red Hat Enterprise Linux 8, download the 19.3 Oracle Database software binaries from Oracle Technology Network (OTN), and then apply the 19.18 release updates (RUs) during the Oracle Database and Oracle Grid Infrastructure installation or upgrade process.
- Installing Oracle Database 19c (19.22) on Oracle Linux 9 and Red Hat Enterprise Linux 9
  Oracle recommends that you install Oracle Database 19c Release 19.22 or later on Oracle Linux 9 and Red Hat Enterprise Linux 9.
- Installing Oracle Database Client 64-bit 19c (19.22) on Oracle Linux 9 and Red Hat Enterprise Linux 9
  Oracle recommends that you install Oracle Database Client 19c Release 19.22 or later on Oracle Linux 9 and Red Hat Enterprise Linux 9.
- Installing Oracle Database Gateway 19c (19.21) on Oracle Linux 9 and Red Hat Enterprise Linux 9
  Oracle recommends that you use Oracle Database Client 19c Release 19.21 or later to install Oracle Database Gateway on Oracle Linux 9 and Red Hat Enterprise Linux 9.
- Installing Oracle Database Client 32-bit 19c (19.19) on Oracle Linux 9 and Red Hat Enterprise Linux 9
  Oracle recommends that you install Oracle Database Client 32-bit 19c Release 19.19 or later on Oracle Linux 9 and Red Hat Enterprise Linux 9.
- Unsupported Products for Oracle Database 19c on Oracle Linux 9 and Red Hat Enterprise Linux 9
  This topic describes products or features that are unavailable for Oracle Database 19c on Oracle Linux 9 and Red Hat Enterprise Linux 9.
- Known Issues and Bugs for Oracle Linux 9 and Red Hat Enterprise Linux 9 on Oracle Database
  This section contains information about issues related to Oracle Linux 9 and Red Hat Enterprise Linux 9 on Oracle Database Client:
- Known Issues and Bugs for Standard Edition High Availability
  This section contains information about issues related to Standard Edition High Availability:

### Certification Information

The latest certification information for Oracle Database 19c is available in My Oracle Support note 1304727.2:

<https://support.oracle.com/epmos/faces/DocumentDisplay?id=1304727.2>

Oracle Linux 7

Starting with Oracle Database 19c, release update (RU) 19.9, Oracle Linux 7.7 with the Unbreakable Enterprise Kernel 6: 5.4.17-2011.4.4.el7uek.x86_64 or later is supported on Linux x86-64.

Refer to [Oracle Database Installation Guide for Linux](../ladbi/supported-oracle-linux-7-distributions-for-x86-64.md) for the preinstallation requirements.

**Parent topic:** Issues Affecting Linux for Oracle Database 19c

### Unsupported Products for Linux

This topic describes products or features that are unavailable for Oracle Database 19c.

In addition to the list of unavailable products or features in this release of Oracle Database 19c, the following product is not supported for Linux:

- IPv6 Networks Support

  The IPv6 based IP addresses to configure the private networks for a cluster is not supported on IBM: Linux on System z. It is currently under testing and the support will be announced after testing is successfully complete.

- Oracle ACFS

  Oracle Automatic Storage Management Cluster File System (Oracle ACFS) is not supported on Oracle Linux 8 and Red Hat Enterprise Linux 8 on Oracle Database 19c release update RU (19.6) and RU (19.7).

**Parent topic:** Issues Affecting Linux for Oracle Database 19c

### Product Support

This topic describes the supported products or features for Oracle Database 19c.

The supported products or features are:

- Database Smart Flash Cache Support

  Database Smart Flash Cache is supported on Oracle Linux.

- Oracle ACFS

  Oracle Automatic Storage Management Cluster File System (Oracle ACFS) is supported on Oracle Linux 9.2 or later and Red Hat Enterprise Linux 9.2 or later on Oracle Database 19c starting with release update RU 19.21 (along with the patch) and later..

  For the latest information about supported platforms and releases, see the Note 1369107.1 on My Oracle Support at [https://support.oracle.com](https://support.oracle.com/)

- Oracle ADVM

  Although Oracle ADVM supports raw disks in Oracle Automatic Storage Management disk groups, Oracle ADVM device special files created through raw are not supported; Oracle ADVM only supports block device special files.

  For the latest information about supported platforms and releases, see the Note 1369107.1 on My Oracle Support at [https://support.oracle.com](https://support.oracle.com/)

- Oracle ASM Filter Driver Support

  Oracle Automatic Storage Management Filter Driver (Oracle ASMFD) is supported only on Linux x86-64.

- Oracle ASM library (Oracle ASMLIB)

  Oracle ASM library (Oracle ASMLIB) is supported on Oracle Linux 6 or later and Red Hat Enterprise Linux 6 or later on Oracle Database 19c starting with release update RU 19.21 (along with the patch) and later.

- Share-based Instance Caging

  Share-based Instance Caging is supported on Oracle Linux.

**Parent topic:** Issues Affecting Linux for Oracle Database 19c

### Linking Applications with Oracle Client Libraries for Linux

You must use the dynamic Oracle client libraries to link the client code on Linux. 

Do not link the static Oracle client libraries.

**Parent topic:** Issues Affecting Linux for Oracle Database 19c

### Preinstallation Requirements for the Linux Platform

Refer to the installation guides for the preinstallation requirements for Oracle Database 19c.

**Parent topic:** Issues Affecting Linux for Oracle Database 19c

### Open Bugs Affecting Linux

This topic contains last-minute features and changes for Oracle Database 19c.

- Bug 26708302

**Parent topic:** Issues Affecting Linux for Oracle Database 19c

#### Bug 26708302

Deinstallation of Oracle Real Application Clusters (Oracle RAC) home on shared Network Attached Storage (NAS) fails to delete the directory `$ORACLE_HOME/deinstall` and returns the following error:

`Failed to delete the directory ``$ORACLE_HOME/deinstall``. Either user has no permission to delete or it is in use.`

Workaround:

Manually delete the `$ORACLE_HOME/deinstall `folder as either the Oracle RAC owner or as root.

**Parent topic:** Open Bugs Affecting Linux

### Known Issues and Bugs for SUSE Linux Enterprise Server 15

This section contains information about issues related to SUSE Linux Enterprise Server 15:

- Bug 29953021
- Bug 29916735
- Bug 29836096
- Bug 29742223
- Bug 30131474

**Parent topic:** Issues Affecting Linux for Oracle Database 19c

#### Bug 29953021

To install Oracle Database software 19.4 on SUSE Linux Enterprise Server 15, download the Oracle Database software binaries from Oracle Technology Network (OTN), and then apply the 19.4 release updates (RUs) during the the Oracle Database and Oracle Grid Infrastructure installation or upgrade process.

Workaround:

During the Oracle Database and Oracle Grid Infrastructure installation process, run the `runInstaller` and `gridSetup.sh` commands with the `-applyRU` and `-applyOneOffs` options to install the latest 19.4 RU for SUSE Linux Enterprise Server 15:

Oracle Grid Infrastructure without Oracle ACFS and Oracle ADVM:

     $ 19.3_grid_home/gridSetup.sh -applyRU 19.4GIRU patch 29708769 -applyOneOffs patch 30171454

Oracle Grid Infrastructure with Oracle ACFS and Oracle ADVM:

    $ 19.3_grid_home/gridSetup.sh -applyRU 19.4GIRU patch 29708769 -applyOneOffs patch 30171454, patch 28321248

Oracle Real Applications Cluster or Oracle Database (with Oracle Restart):

    $ 19.3_dbhome/runInstaller -applyRU 19.4GIRU patch 29708769 -applyOneOffs patch 30171454

Single-instance Oracle Database:

    $ 19.3_dbhome/runInstaller -applyRU 19.4DBRU patch 29834717 -applyOneOffs patch 30083976

**Parent topic:** Known Issues and Bugs for SUSE Linux Enterprise Server 15

#### Bug 29916735

On SUSE Linux Enterprise Server 15, after upgrading Oracle Grid Infrastructure to 19.4 GIRU, CPU usage increases when you run OSWatcher.

Workaround:

Perform the following steps:

1.  Enter the following command to stop OSWatcher from Oracle Trace File Analyzer (Oracle TFA):
        $ grid_home/bin/tfactl stop  oswbb to stop
2.  Add `disown -a` to the main loop inside `OSWatcher.sh`.
3.  Set `ulimit` to a sufficiently low value for the user running OSWatcher. 

This issue is fixed in OSWatcher 8.3.1.

See My Oracle Support Note 301137.1 for more information:

<https://support.oracle.com/rs?type=doc&id=301137.1>

**Parent topic:** Known Issues and Bugs for SUSE Linux Enterprise Server 15

#### Bug 29836096

`libstdc++33` package missing error during Oracle Instant Client installation.

Workaround:

In the Perform Prerequisite Checks screen, select Ignore All and proceed with the installation.

For non-interactive or silent installations, run the following command:

    $./runInstaller -ignorePrereq

**Parent topic:** Known Issues and Bugs for SUSE Linux Enterprise Server 15

#### Bug 29742223

If you install single instance Oracle Database 19c on SUSE Linux Enterprise Server 15 or SUSE Linux Enterprise Server 12 SP3 with 19.8 or later DBRU, then you may encounter a prerequisite error for the `libstdc++33-3.3.3-62.1` package.

Workaround 1:

The `libstdc++33-3.3.3-62.1` package is not required on SUSE Linux Enterprise Server 15 or SUSE Linux Enterprise Server 12 SP3.

In the Perform Prerequisite Checks screen, select Ignore All and proceed with the installation.

Workaround 2:

Apply 19c Oracle Clusterware Release Update (OCWRU) that is bundled in the 19c Oracle Grid Infrastructure Release Update (GIRU) along with Oracle Database 19c Release Update (DBRU) 19.8 or later.

**Parent topic:** Known Issues and Bugs for SUSE Linux Enterprise Server 15

#### Bug 30131474

`libgfortran` package missing error during Oracle Database 19.4 installation on SUSE Linux Enterprise Server 15

Workaround:

Ignore the warning and ensure that you install the `libgfortran4-7.3.1+r258812-2.15.x86_64` package on the system.

**Parent topic:** Known Issues and Bugs for SUSE Linux Enterprise Server 15

### Unsupported Products for Oracle Database 19c on Oracle Linux 8

The following products or features are unavailable for Oracle Database 19c on Oracle Linux 8.

- DBnest

**Parent topic:** Issues Affecting Linux for Oracle Database 19c

### Known Issues and Bugs for Oracle Linux 8 and Red Hat Enterprise Linux 8

This section contains information about issues related to Oracle Linux 8 and Red Hat Enterprise Linux 8:

- Bug 30878668
- Bug 30445619
- Bug 36567521
- Bug 36565959
- Bug 29772579

**Parent topic:** Issues Affecting Linux for Oracle Database 19c

#### Bug 30878668

The `sudo` option for running root configuration scripts does not work during Oracle Database 19c or Oracle Grid Infrastructure 19c installations on Oracle Linux 8 or Red Hat Enterprise Linux 8 systems.

Workaround:

Run the root configuration scripts manually as the `root` user.

**Parent topic:** Known Issues and Bugs for Oracle Linux 8 and Red Hat Enterprise Linux 8

#### Bug 30445619

On Oracle Linux 8 or Red Hat Enterprise Linux 8, C++ applications built with `g++8` cannot be used with Oracle C++ Call Interface (OCCI).

Workaround:

For building applications with `g++8`, use the following compilation options:

    -D_GLIBCXX_USE_CXX11_ABI=0 -Wno-narrowing

**Parent topic:** Known Issues and Bugs for Oracle Linux 8 and Red Hat Enterprise Linux 8

#### Bug 36567521

All `Pro*C` demos fail during compilation on Oracle Database 19c on Oracle Linux 8 and Red Hat Enterprise Linux 8.

Workaround:

Manually add the `gcc include path` in the `pcscfg.cfg` file with the `sys_include` option.

    sys_include=/usr/lib/gcc/x86_64-redhat-linux/8/include

**Parent topic:** Known Issues and Bugs for Oracle Linux 8 and Red Hat Enterprise Linux 8

#### Bug 36565959

On Oracle Linux 8 or Red Hat Enterprise Linux 8, C++ applications built with `g++11` cannot be used with Oracle C++ Call Interface (OCCI).

Workaround:

For building applications with `g++11`, use the following compilation options:

    -D_GLIBCXX_USE_CXX11_ABI=0 -Wno-narrowing

**Parent topic:** Known Issues and Bugs for Oracle Linux 8 and Red Hat Enterprise Linux 8

#### Bug 29772579

`compat-libcap1-1.10` package missing error during single-instance Oracle Database and Oracle Database Client installations on Oracle Linux 8 and Red Hat Enterprise Linux 8.

Workaround:

In the Perform Prerequisite Checks screen, for the `compat-libcap1-1.10` missing check, select Ignore All, and click Install to continue with the installation.

**Note:**

Ensure that you fix all other checks and issues that are listed in the screen.

**Parent topic:** Known Issues and Bugs for Oracle Linux 8 and Red Hat Enterprise Linux 8

### Installing Oracle Database 19c on Oracle Linux 8 and Red Hat Enterprise Linux 8

To install Oracle Database 19c on Oracle Linux 8 or Red Hat Enterprise Linux 8, download the 19.3 Oracle Database software binaries from Oracle Technology Network (OTN), and then apply the 19.18 release updates (RUs) during the Oracle Database and Oracle Grid Infrastructure installation or upgrade process.

**Note:**

- Starting with Oracle Database 19c Release 19.21, Oracle Linux 8.8 with the Unbreakable Enterprise Kernel 7 is supported.
- Starting with Oracle Grid Infrastructure 19c Release 19.23, Oracle Linux 8.8 with the Unbreakable Enterprise Kernel 7 is supported.

Installation Process:

During the Oracle Database and Oracle Grid Infrastructure installation process, run the `runInstaller` and `gridSetup.sh` commands with the `-applyRU` and `-applyOneOffs` options to install the latest 19.18 RU for Oracle Linux 8 and Red Hat Enterprise Linux 8:

Single-instance Oracle Database (19.18):

    $ export CV_ASSUME_DISTID=OL7
    $ 19.3_dbhome/runInstaller -applyRU 19.18DBRU patch 34765931 location

Oracle Grid Infrastructure (19.18):

    $ 19.3_grid_home/gridSetup.sh -applyRU 19.18GIRU patch 34762026 location

Oracle Real Applications Cluster (19.18):

    $ 19.3_dbhome/runInstaller -applyRU 19.18GIRU patch 34762026 location

**Parent topic:** Issues Affecting Linux for Oracle Database 19c

### Installing Oracle Database 19c (19.22) on Oracle Linux 9 and Red Hat Enterprise Linux 9

Oracle recommends that you install Oracle Database 19c Release 19.22 or later on Oracle Linux 9 and Red Hat Enterprise Linux 9.

To install Oracle Database 19c on Oracle Linux 9 and Red Hat Linux 9, download the 19.3 Oracle Database software binaries from the Oracle website, and then apply the 19.22 release updates (RUs) during the installation process.

Installation Process:

During the Oracle Database and Oracle Grid Infrastructure installation process, run the `runInstaller` and `gridSetup.sh` commands with the `-applyRU` and `-applyOneOffs` options to install the latest 19.22 RU for Oracle Linux 9 and Red Hat Enterprise Linux 9.

Oracle Grid Infrastructure (19.22):

1.  Unzip the 19.3.0.0.0 Oracle Grid Infrastructure gold image.

2.  Copy the OPatch utility version 12.2.0.1.40 or later from My Oracle Support patch 6880880 by selecting the 19.0.0.0.0 release.

3.  Install Oracle Grid Infrastructure by running gridSetup.sh with applyRU to create and install Oracle Grid Infrastructure 19.22 by running the following command:

    From the 19.3 GI home, run

    \$ gridSetup.sh -applyRU \<19.22 GIRU Patch 35940989 location\>

Oracle Real Application Clusters (19.22):

1.  Unzip the 19.3.0.0.0 Oracle Database gold image.
2.  Copy the OPatch utility version 12.2.0.1.40 or later from My Oracle Support patch 6880880 by selecting the 19.0.0.0.0 release.
3.  Install Oracle Real Applications Cluster (Oracle RAC) software with \$ 19.3 on-prem_db\_ image/runInstaller -applyRU \<19.22 GIRU Patch 35940989 location\>
4.  Run Oracle Database Configuration Assistant (DBCA) to create the Oracle Real Applications Cluster (Oracle RAC).

Single-instance Oracle Database (19.22):

1.  Set the environment variable CV_ASSUME_DISTID to OL7 (`$export CV_ASSUME_DISTID=OL7`).
2.  Unzip the 19.3.0.0.0 Oracle Database gold image.
3.  Copy the OPatch utility version 12.2.0.1.40 or later from My Oracle Support patch 6880880 by selecting the 19.0.0.0.0 release.
4.  Install Single-instance Oracle Database with \$ 19.3 on-prem_db\_ image/runInstaller -applyRU \<19.22 DBRU Patch 35943157 location\>

Oracle Restart with Single-instance Oracle Database (19.22):

Oracle Restart (19.22)

1.  Unzip the 19.3.0.0.0 Oracle Grid Infrastructure gold image.
2.  Copy the OPatch utility version 12.2.0.1.40 or later from My Oracle Support patch 6880880 by selecting the 19.0.0.0.0 release.
3.  Install Oracle Grid Infrastructure with \$ 19.3 on-prem_grid\_ image/gridSetup.sh applyRU \<19.22 GIRU Patch 35940989 location\>

Single-instance Oracle Database on Oracle Automatic Storage Management (Oracle ASM) with Oracle Restart (19.22)

1.  Unzip the 19.3.0.0.0 Oracle Database gold image.
2.  Copy the OPatch utility version 12.2.0.1.40 or later from My Oracle Support patch 6880880 by selecting the 19.0.0.0.0 release.
3.  Install Single-instance Oracle Database with \$ 19.3 on-prem_db\_ image/runInstaller applyRU \<19.22 GIRU Patch 35940989 location\>

**Parent topic:** Issues Affecting Linux for Oracle Database 19c

### Installing Oracle Database Client 64-bit 19c (19.22) on Oracle Linux 9 and Red Hat Enterprise Linux 9

Oracle recommends that you install Oracle Database Client 19c Release 19.22 or later on Oracle Linux 9 and Red Hat Enterprise Linux 9.

To install Oracle Database Client 19c on Oracle Linux 9 and Red Hat Linux 9, download the 19.3 Oracle Database Client software binaries from the Oracle website, and then apply the 19.22 release updates (RUs) during the installation process.

During the Oracle Database Client gold image installation process, run the `runInstaller` command with the `-applyRU` and `-applyOneOffs` options to install the latest 19.22 RU for Oracle Linux 9 and Red Hat Enterprise Linux 9.

Oracle Database Client (19.22) Gold Image Installation

    $ export CV_ASSUME_DISTID=OL7
    $ 19.3_clienthome/runInstaller -applyRU <19.22DBRU patch 35943157 location>

During the Oracle Database Client gold image installation process, run the `runInstaller` command with the `-applyRU` and `-applyOneOffs` options to install the latest 19.22 RU for Oracle Linux 9 and Red Hat Enterprise Linux 9.

Oracle Database Client (19.22) Shiphome-based Installation

    $ export CV_ASSUME_DISTID=OL7
    $ 19.3_clienthome/runInstaller

**Note:**

- Ignore the linking errors during 19.3 client installations and 19.22DBRU.
- After the 19.3 Oracle Database Client installation is complete, apply the `19.22DBRU patch 35943157`.

During the Oracle Database Client shiphome based installation process, run the `runInstaller` command to install the latest 19.22 RU for Oracle Linux 9 and Red Hat Enterprise Linux 9.

Oracle Database Global Service Manager (19.22) Shiphome-based Installation

    $ export CV_ASSUME_DISTID=OL7
    $ 19.3_gsmhome/runInstaller

**Note:**

- Ignore the linking errors during 19.3 client installations and 19.22DBRU.
- After the 19.3 Oracle Database Global Service Manager installation is complete, apply the `19.22DBRU patch 35943157`.

**Note:**

For all Client and GSM installations, after you apply a patch, ensure that you run the following command to relink executables and libraries in `$ORACLE_HOME`:

    $ORACLE_HOME/bin/relink as_installed

**Parent topic:** Issues Affecting Linux for Oracle Database 19c

### Installing Oracle Database Gateway 19c (19.21) on Oracle Linux 9 and Red Hat Enterprise Linux 9

Oracle recommends that you use Oracle Database Client 19c Release 19.21 or later to install Oracle Database Gateway on Oracle Linux 9 and Red Hat Enterprise Linux 9.

To install Oracle Database Gateway 19c on Oracle Linux 9 and Red Hat Linux 9, download the 19.3 Oracle Database Client software binaries from the Oracle website, and then apply the 19.21 release updates (RUs) during the installation process.

#### Oracle Database Gateway (19.21) Shiphome-based Installation

    $ export CV_ASSUME_DISTID=OL7
    $ 19.3_gatewayshome/runInstaller

**Note:**

- Ignore the linking errors during 19.3 Oracle Database Gateway installation and 19.21DBRU.
- After the 19.3 Oracle Database Gateway installation is complete, apply the `19.21DBRU patch 35643107, 19.21OneOff patch 35954820, and 19.21OneOff patch 35578393`.
- Apply the `19.0.0.0.0 OneOff patch 35578393` if APPC component is installed during the Oracle Database Gateway installation.

**Note:**

For Gateway installations, after you apply a patch, ensure that you run the following command to relink executables and libraries in `$ORACLE_HOME`:

    $ORACLE_HOME/bin/relink as_installed

**Parent topic:** Issues Affecting Linux for Oracle Database 19c

### Installing Oracle Database Client 32-bit 19c (19.19) on Oracle Linux 9 and Red Hat Enterprise Linux 9

Oracle recommends that you install Oracle Database Client 32-bit 19c Release 19.19 or later on Oracle Linux 9 and Red Hat Enterprise Linux 9.

To install Oracle Database Client 19c on Oracle Linux 9 and Red Hat Linux 9, download the 19.3 Oracle Database Client software binaries from the Oracle website, and then apply the 19.19 release updates (RUs) during the installation process.

During the Oracle Database Client gold image installation process, run the `runInstaller` command with the `-applyRU` and `-applyOneOffs` options to install the latest 19.19 RU for Oracle Linux 9 and Red Hat Enterprise Linux 9.

#### Oracle Database Client 32-bit (19.19) Gold Image Installation

    $ export CV_ASSUME_DISTID=OL7
    $ 19.3_clienthome/runInstaller -applyRU <19.19DBRU patch 35042068 location> -applyOneOffs <19.19OneOff patch 35700050 location>

During the Oracle Database Client shiphome based installation process, run the `runInstaller` command to install the latest 19.19 RU for Oracle Linux 9 and Red Hat Enterprise Linux 9.

#### Oracle Database Client 32-bit (19.19) Shiphome-based Installation

    $ export CV_ASSUME_DISTID=OL7
    $ 19.3_clienthome/runInstaller

**Note:**

- Ignore the linking errors during 19.3 client installations and 19.19DBRU.
- After the 19.3 Oracle Database Client installation is complete, apply the `19.19DBRU patch 35042068 and 19.19OneOff patch 35700050`.

**Note:**

For 32-bit Client installations, after you apply a patch, ensure that you run the following command to relink executables and libraries in `$ORACLE_HOME`:

    $ORACLE_HOME/bin/relink as_installed

**Parent topic:** Issues Affecting Linux for Oracle Database 19c

### Unsupported Products for Oracle Database 19c on Oracle Linux 9 and Red Hat Enterprise Linux 9

This topic describes products or features that are unavailable for Oracle Database 19c on Oracle Linux 9 and Red Hat Enterprise Linux 9.

- DBnest
- Oracle Machine Learning for R (OML4R)

**Parent topic:** Issues Affecting Linux for Oracle Database 19c

### Known Issues and Bugs for Oracle Linux 9 and Red Hat Enterprise Linux 9 on Oracle Database

This section contains information about issues related to Oracle Linux 9 and Red Hat Enterprise Linux 9 on Oracle Database Client:

- Bug 35521990
- Bug 35547711
- Bug 35448216
- Bug 35584316
- Bug 35614058
- Bug 36347606
- Bug 36513962

**Parent topic:** Issues Affecting Linux for Oracle Database 19c

#### Bug 35521990

During Oracle Database Client 32-bit installation on Oracle Linux 9 and Red Hat Enterprise Linux 9, the following warning messages is displayed:

    /bin/ld: libirc.a(fast_memcpy_pp.o):
    warning: relocation in read-only section `.text'

    INFO:
    /bin/ld: warning: creating DT_TEXTREL in a shared object

    INFO:
    /bin/ld: libirc.a(sse2_strspn.o): warning:
    relocation in read-only section `.text'

    INFO:
    /bin/ld: warning: creating DT_TEXTREL in a shared object

The following warning messages is displayed during `19.19OneOff patch 35700050`:

    OPatch found the word "warning" in the stderr of the make command.
    Please look at this stderr. You can re-run this make command.
    Stderr output:
    /bin/ld: $ORACLE_HOME/lib/libirc.a(fast_memcpy_pp.o):warning: relocation in read-only section `.text'
    /bin/ld: warning: creating DT_TEXTREL in a shared object
    /bin/ld: $ORACLE_HOME/lib/libirc.a(sse2_strspn.o): warning: relocation in read-only section `.text'
    /bin/ld: warning: creating DT_TEXTREL in a shared object

Workaround:

Ignore the warning messages.

**Parent topic:** Known Issues and Bugs for Oracle Linux 9 and Red Hat Enterprise Linux 9 on Oracle Database

#### Bug 35547711

`compat-libcap1-1.10` and `compat-libstdc++-33` packages missing error during Oracle Database Client 32-bit installation on Oracle Linux 9 and Red Hat Enterprise Linux 9.

Workaround:

In the Perform Prerequisite Checks screen, for the `compat-libcap1-1.10` and `compat-libstdc++-33` missing checks, select Ignore All, and click Install to continue with the installation.

**Note:**

Ensure that you fix all other checks and issues that are listed in the screen.

**Parent topic:** Known Issues and Bugs for Oracle Linux 9 and Red Hat Enterprise Linux 9 on Oracle Database

#### Bug 35448216

`compat-libcap1-1.10` package missing error during Oracle Database Client 64-bit installation on Oracle Linux 9 and Red Hat Enterprise Linux 9.

Workaround:

In the Perform Prerequisite Checks screen, for the `compat-libcap1-1.10` missing check, select Ignore All, and click Install to continue with the installation.

**Note:**

Ensure that you fix all other checks and issues that are listed in the screen.

**Parent topic:** Known Issues and Bugs for Oracle Linux 9 and Red Hat Enterprise Linux 9 on Oracle Database

#### Bug 35584316

On Oracle Linux 9 or Red Hat Enterprise Linux 9, C++ applications built with `g++11` cannot be used with Oracle C++ Call Interface (OCCI).

Workaround:

For building applications with `g++11`, use the following compilation options:

    -D_GLIBCXX_USE_CXX11_ABI=0 -Wno-narrowing

**Parent topic:** Known Issues and Bugs for Oracle Linux 9 and Red Hat Enterprise Linux 9 on Oracle Database

#### Bug 35614058

Static Client linking demos fail during compilation on Oracle Database Client 19c on both 32-bit and 64-bit versions on Oracle Linux 9 and Red Hat Enterprise Linux 9.

Workaround:

Oracle Database Client 19c supports only Dynamic Client linking demos on both 32-bit and 64-bit versions on Oracle Linux 9 and Red Hat Enterprise Linux 9.

**Parent topic:** Known Issues and Bugs for Oracle Linux 9 and Red Hat Enterprise Linux 9 on Oracle Database

#### Bug 36347606

During Oracle Database Client 64-bit installation on Oracle Linux 9 and Red Hat Enterprise Linux 9, the silent installation fails.

Workaround:

Perform the following steps when installing Oracle Database Client 64-bit using the silent installation method:

1.  Extract the `p36347606_1922000_Linux-x86-64.zip` and extract `client.zip` to a temporary (or bootstrap) location.

2.  Run the command:

        ./runInstaller -silent -ignorePrereq -showProgress -waitforcompletion -responseFile <response file location>

**Parent topic:** Known Issues and Bugs for Oracle Linux 9 and Red Hat Enterprise Linux 9 on Oracle Database

#### Bug 36513962

During Oracle Database Client 32-bit installation on Oracle Linux 9 and Red Hat Enterprise Linux 9, the silent installation method fails.

Workaround:

Perform the following steps when installing Oracle Database Client 32-bit using the silent installation method:

1.  Extract the `p36513962_1922000DBRU_LINUX.zip` and extract `client.zip` to a temporary (or bootstrap) location.

2.  Run the command:

        ./runInstaller -silent -ignorePrereq -showProgress -waitforcompletion -responseFile <response file location>

**Parent topic:** Known Issues and Bugs for Oracle Linux 9 and Red Hat Enterprise Linux 9 on Oracle Database

### Known Issues and Bugs for Standard Edition High Availability

This section contains information about issues related to Standard Edition High Availability:

- Bug 30821297
- Bug 30979062
- Bug 30992915
- Bug 31114977
- Bug 31128434
- Bug 31128452
- Bug 31146826
- Bug 31156506
- Bug 31188168
- Bug 31264160

**Parent topic:** Issues Affecting Linux for Oracle Database 19c

#### Bug 30821297

Oracle Database Standard Edition 2 allows you to create more than one pluggable database (PDB) in a multitenant container database (CDB). However, when you use the Oracle Database Configuration Assistant (Oracle DBCA) to create a second PDB, you receive the following error:

    [FATAL] [DBT-11506] Creation of more than one PDB requires Enterprise Edition license.

Workaround:

Create the additional PDB using the SQL statement `CREATE PLUGGABLE DATABASE`.

**Related Topics**

- [Oracle Multitenant Administrator’s Guide](../multi/creating-and-configuring-a-cdb.md)

**Parent topic:** Known Issues and Bugs for Standard Edition High Availability

#### Bug 30979062

When you use the `srvctl relocate database` command to initiate the relocation of a database configured with Standard Edition High Availability, and if the destination-configured node does not have an available Oracle Database home, then the relocation fails as expected but with error messages that do not include the reason for the failure.

This issue will be fixed in a future Oracle Database 19c release update.

Workaround:

None.

**Parent topic:** Known Issues and Bugs for Standard Edition High Availability

#### Bug 30992915

When you use Oracle Database Configuration Assistant (Oracle DBCA) to create a single-instance database on an Oracle Clusterware node, the database is registered with Oracle Clusterware. However, the command output incorrectly says the following:

    Registering database with Oracle Restart

Workaround:

None.

**Parent topic:** Known Issues and Bugs for Standard Edition High Availability

#### Bug 31114977

When you relocate Oracle Database configured with Standard Edition High Availability that has active database services, the `srvctl status service` command on that database displays a blank list of instance that has the services running. However, the services are running on the database instance.

Workaround:

None.

**Parent topic:** Known Issues and Bugs for Standard Edition High Availability

#### Bug 31128434

When you use the `srvctl relocate database` command to initiate the relocation of a database configured with Standard Edition High Availability, and if Oracle Database has a service registered, then the shutdown of the database instance is suspended for a period of time due to the mount lock being held.

The registered database services are not accessible when the database instance is suspended and the Oracle Database instance stops eventually on the current node and starts on the destination node.

Workaround:

  Use a sequence of `srvctl stop database` commands followed by the `srvctl start database -node ``destination node` commands to avoid shutdown suspension.  

**Parent topic:** Known Issues and Bugs for Standard Edition High Availability

#### Bug 31128452

When you run the `srvctl config service` command for an Oracle Database with Standard Edition High Availability configured and its services registered,  a `Java NULL pointer exception` occurs at the end of the output for the first service.

This issue will be fixed in a future Oracle Database 19c release update.

Workaround:

None.

**Parent topic:** Known Issues and Bugs for Standard Edition High Availability

#### Bug 31146826

When you configure Standard Edition High Availability for a single-instance Oracle Database 19c Release Update (RU) 19.7 that does not have any database services registered, you will observe a local restart when the instance is abnormally terminated. However, after a service is added to the database, you do not observe the local restart. Instead, the database fails over immediately when it is abnormally terminated.

This issue will be fixed in a future Oracle Database 19c release update.

Workaround:

None.

**Parent topic:** Known Issues and Bugs for Standard Edition High Availability

#### Bug 31156506

If Oracle base of the Oracle Database home is the same as Oracle base of the Oracle Grid Infrastructure home, then if the user adds a new node to the cluster, the Oracle Database home user loses access permissions to some of the subdirectories under Oraclebase of the Oracle Database home.

Workaround:

Use distinct directories as Oracle base for the Oracle Grid Infrastructure and Oracle Database installations.

**Parent topic:** Known Issues and Bugs for Standard Edition High Availability

#### Bug 31188168

When you use the `srvctl relocate database -help` command from a Standard Edition single-instance Oracle Database 19c home, the prompt incorrectly displays usage and help messages with the mention of Oracle Real Application Clusters One Node (Oracle RAC One Node). Starting with Oracle Database 19c Release Update (RU) 19.7, this command applies to Standard Edition High Availability and must contain the corresponding usage and help messages.

This issue will be fixed in a future Oracle Databse 19c release update.

Workaround:

**Related Topics**

- [Oracle Database Admninistrator's Guide](../admin/creating-and-configuring-an-oracle-database.md)
- [Oracle Clusterware Administration and Deployment Guide](../cwadd/server-control-command-reference.md)

**Parent topic:** Known Issues and Bugs for Standard Edition High Availability

#### Bug 31264160

Starting with Oracle Database 19c Release Update (RU) 19.7, you use the `srvctl` add or modify database commands to configure Standard Edition High Availability by specifying the `-node` option with a node list of more than one node. However, the usage messages from these commands, such as when running from an Oracle Database Standard Edition 2 database home with the `-help` option, do not show this usage.

This issue will be fixed in a future Oracle Database 19c release update.

Workaround:

**Related Topics**

- [Oracle Database Admninistrator's Guide](../admin/creating-and-configuring-an-oracle-database.md)
- [Oracle Clusterware Administration and Deployment Guide](../cwadd/server-control-command-reference.md)

**Parent topic:** Known Issues and Bugs for Standard Edition High Availability
