This section provides information about the hardware and software requirements and the installation procedure for Oracle Database Gateway for ODBC.

To install Oracle Database Gateway for ODBC, follow these steps:

1.  Ensure that the system meets all of the hardware and software requirements specified in System Requirements for Oracle Database Gateway for ODBC.

2.  Run the Oracle Universal Installer.

    See Step Through the Oracle Universal Installer for more information about running the Oracle Universal Installer.

    Oracle Universal Installer is a menu-driven utility that guides you through the installation of Oracle Database Gateway for ODBC by prompting you with action items. The action items and the sequence in which they appear depend on your platform.

    See Table 10-2 for a description of the installation procedure of Oracle Database Gateway for ODBC.

### System Requirements for Oracle Database Gateway for ODBC

This section provides information about the hardware and software requirements for Oracle Database Gateway for ODBC. It contains the following sections:

- Hardware Requirements

- Software Requirements

Refer to the [Oracle Database Installation Guide for Microsoft Windows](../ntdbi/index.md) and to the certification matrix on My Oracle Support for the most up-to-date list of certified hardware platforms and operating system version requirements to operate the gateway for your system. The My Oracle Support Web site can be found at:

<https://support.oracle.com>

#### Hardware Requirements

Table 10-1 lists the minimum hardware requirements for Oracle Database Gateway for ODBC.

Table 10-1 Hardware Requirements for Oracle Database Gateway for ODBC

| Requirement      | For Microsoft Windows (64-bit)          |
|:-----------------|:----------------------------------------|
| Total disk space | 5 GB                                    |
| Physical Memory  | Minimum of 1 GB                         |
| Virtual memory   | Double the amount of RAM                |
| Video adapter    | 256 colors                              |
| Processor        | AMD64, or Intel Extended memory (EM64T) |

##### Checking the Hardware Requirements

To ensure that the system meets the minimum requirements, follow these steps:

1.  Determine the physical RAM size. For a computer using Microsoft Windows 2000, for example, open System in the control panel and select the General tab. If the size of the physical RAM installed in the system is less than the required size, then you must install more memory before continuing.
2.  Determine the size of the configured swap space (also known as paging file size). For a computer using Microsoft Windows 2000, for example, open System in the control panel, select the Advanced tab, and click Performance Options.
    If necessary, then see your operating system documentation for information about how to configure additional swap space.
3.  Determine the amount of free disk space on the system. For a computer using Microsoft Windows 2000, for example, open My Computer, right-click the drive where the Oracle software is to be installed, and select Properties.
4.  Determine the amount of disk space available in the `temp` directory. This is equivalent to the total amount of free disk space, minus what will be needed for the Oracle software to be installed.
    If there is less than 125 MB of disk space available in the `temp` directory, then first delete all unnecessary files. If the temp disk space is still less than 125 MB, then set the `TEMP` or `TMP` environment variable to point to a different hard drive. For a computer using Microsoft Windows 2000, for example, open the System control panel, select the Advanced tab, and click Environment Variables.

#### Software Requirements

Oracle Database Gateway for ODBC is supported on the following Microsoft Windows (64-bit) operating systems:

- Microsoft Windows Server 2003 - all x64 editions

- Microsoft Windows Server 2003 R2 - all x64 editions

- Microsoft Windows XP Professional x64 Edition

- Microsoft Windows Vista x64 - Business, Enterprise, and Ultimate editions

- Microsoft Windows 2008 x64

##### Certified Configurations

For the latest certified configuration refer to the OTN Web site:

    http://www.oracle.com/technetwork/database/gateways/index.html

### Step Through the Oracle Universal Installer

Table 10-2 describes the installation procedure for Oracle Database Gateway for ODBC.

Table 10-2 The Oracle Universal Installer: Steps for Installing Oracle Database Gateway for ODBC

| Screen                                                   | Response                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|:---------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Oracle Universal Installer: Welcome                      | Click Next.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Oracle Universal Installer: Specify Home Details         | Specify a name for the installation in the Name field. You can also choose not to edit the default setting of the Name field of the Specify Home Details screen.<br>The Path field in the Specify Home Details screen is where you specify the destination for your installation. You need not edit the path specification in the Path field. The default setting for this field points to `ORACLE_HOME`. After you set the fields in the Specify Home Details screen as necessary, click Next to continue. After loading the necessary information from the installation, the Oracle Universal Installer displays the Available Products screen. |
| Oracle Universal Installer: Available Product Components | a\. Select Oracle Database Gateway for ODBC 12.2.<br>b. Click Next.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Oracle Universal Installer: Summary                      | The Installation Summary screen enables you to review a tree list of options and components for this installation. Click Install to start installation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Oracle Net Configuration Assistant: Welcome              | Click Cancel.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Oracle Net Configuration Assistant:                      | Click Yes.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| Oracle Universal Installer: Configuration Tools          | Click Exit.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Exit                                                     | The final screen of the Oracle Universal Installer is the End of Installation screen. Click Exit to exit the installer.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |

The gateway is now installed.

When the Oracle Universal Installer confirms that the installation is complete, verify that the installation procedure was successful. To do this, read the contents of the installation log file, which is located in the `C:\Program Files\Oracle\Inventory\logs` directory.

The default file name is `InstallActions``YYYY-MM-DD_HH-mm-SS-AM/``PM``.log`, where:

- `YYYY` is year
- `MM` is month
- `DD` is day
- `HH` is hour
- `mm` is minute
- `SS` is seconds
- `AM/PM` is daytime or evening
-

Each of these variables in the log file name represents the date and time the product was installed.
