Depending on the products that you intend to install, verify that the following software is installed on the system.

| Item                                                         | Requirement                                                                                                                                                                                                      |
|:-------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Operating system                                             | The following or later versions of the operating system are supported for Oracle Database 19c:<br>• Apple Mac OS X 10.13.5 (High Sierra)<br>• Apple Mac OS X 10.14 (Mojave)<br>• Apple Mac OS X 10.15 (Catalina) |
| Tools                                                        | • Xcode 9.4<br>• GNU C compiler (gcc) version 4.2.1 or later<br>• This version of gcc is included in Xcode 9.4 or later.<br>• Apple LLVM version 9.1.0<br>• JDK 1.8.0_172.jdk                                    |
| Pro\*C/C++, Oracle Call Interface, Oracle C++ Call Interface | The version of the GNU C and C++ compiler listed previously is supported for use with these products.                                                                                                            |
| Oracle JDBC/OCI Drivers                                      | You must use JDBC-OCI 1.8.0 or later versions with the JNDI extension.                                                                                                                                           |
| Oracle ODBC Driver                                           | Download and install unixODBC-2.3.4 or later at [http://www.unixodbc.org](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/mxcli&id=unix_odb)                                  |

To ensure that the system meets these requirements:

1.  To determine the operating system version, enter the following command:

        $ sw_vers

    The output of this command must be similar to the following:

        ProductName:    Mac OS X
        ProductVersion: 10.13.5
        BuildVersion:   17F77

    **Note:**

    Only the versions listed in the previous table are supported. Do not install the software on other versions of Apple Mac OS X.

2.  To determine if the required version of `gcc` is installed, enter the following command:

        $ gcc -v

    This command returns output similar to the following:

        Configured with: --prefix=/Applications/Xcode.app/Contents/Developer/usr --with-gxx-include-dir=/usr/include/c++/4.2.1
        Apple LLVM version 9.1.0 (clang-902.0.39.2)
        Target: x86_64-apple-darwin17.6.0
        Thread model: posix
        InstalledDir: /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin

    If the required version (including the date and build number) or a later version is not installed, then download and install Xcode 9.4 or later. You can download this software from the Apple Developer Connection website at

    [`https://developer.apple.com/`](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/mxcli&id=dev_apple)

3.  To determine if the correct version of Xcode is installed, enter the following command:

        $ /usr/bin/xcodebuild -version

    This commands returns output similar to the following:

        Xcode 9.4
        Build version 9F1027a

    If the required version (including the date and build number) or a later version is not installed, then download and install Xcode 5.0.2 or later. You can download this software from the Apple Developer Connection website at

    [`https://developer.apple.com/`](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/mxcli&id=dev_apple)

- [Instant Client Light Requirements](instant-client-light-requirements.md)

**Parent topic:** [Oracle Database Instant Client Preinstallation Tasks](oracle-database-client-preinstallation-tasks.md)
