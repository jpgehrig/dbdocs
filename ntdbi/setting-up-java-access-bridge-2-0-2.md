## Setting Up Java Access Bridge 2.0.2

Learn how to install and configure Java Access Bridge 2.0.2 for Windows after installing Oracle components.

To set up Java Access Bridge 2.0.2 on a Windows 64-bit operating system, follow these steps:

1.  Go to Java Standard Edition 2 (Java SE) Downloads page to download the latest build of JDK 8:
    [`http://docs.oracle.com`](http://docs.oracle.com)
2.  Install JDK 8 after accepting the Oracle license agreement.
    **Note:**

    You must have administrator privileges to install JDK on Windows.
3.  Download and install screen reader, JAWS:
    [`http://www.freedomscientific.com/downloads/jaws/JAWS-downloads.asp`](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/ntdbi&id=freedom_scientific_downloads)
4.  Press Windows key+U to open the Ease of Access Center, and select Use the computer without a display.
5.  Select Enable Accessbridge check box. Click Save to save the changes.
6.  Download Java Access Bridge 2.0.2:
    [`http://docs.oracle.com`](http://docs.oracle.com)

    Download the `accessbridge-2_0_2-fcs-bin-b06.zip` file, after accepting the Oracle license agreement.
7.  Extract `accessbridge-2.0.2` to a directory on your system where you plan to install Java Access Bridge. For example, name the directory as follows:
        AB_HOME
8.  Copy `AB_HOME``\WindowsAccessBridge-64.dll` to `c:\windows\system32` and start the screen reader.
9.  Open the command prompt and navigate to `setup.exe` file.
10. Run the following command once you are in the `Disk1` directory:
    `setup.exe `

    Oracle Universal Installer starts and JAWS is able to read all prompts and controls on the screen.
11. Once you click the Install button, you must open Windows Explorer to see the directory where the database is installed (`DRIVE_LETTER:\app\username\product\19.0.0\``dbhome_1`), until the JDK folder is created. Once the JDK folder is created, you must copy the files from the Java Access Bridge source location to the JDK destination folder. Copying these files enables accessibility for both the Oracle Database Configuration Assistant and Oracle Net Configuration Assistant.
    Table A-1 Copy Files to JDK Directory on Windows 64-Bit

    | Copy                                 | To                           |
    |:-------------------------------------|:-----------------------------|
    | `AB_HOME``\JavaAccessBridge-64.dll`  | `dbhome_1``\jdk\jre\bin`     |
    | `AB_HOME``\JAWTAccessBridge-64.dll`  | `dbhome_1``\jdk\jre\bin`     |
    | `AB_HOME``\Accessibility.properties` | `dbhome_1``\jdk\jre\lib`     |
    | `AB_HOME``\Access-bridge-64.jar`     | `dbhome_1``\jdk\jre\lib\ext` |
    | `AB_HOME``\jaccess.jar`              | `dbhome_1``\jdk\jre\lib\ext` |

**Parent topic:** [Installing Java Access Bridge](installing-java-access-bridge.md)
