## About the Oracle Instant Client SDK

Learn about the software development kit (SDK) development tools for Oracle Instant Client.

The SDK is a set of development tools that you can use to create applications for Oracle Instant Client. The SDK is available for download as an RPM or a zip file for Oracle Linux x86-64 and Arm platforms. Here are some examples of these RPM and zip files:

### For Linux x86-64

- RPM (Oracle Linux 9): `oracle-instantclient19.27-devel-19.27.0.0.0-1.el9.x86_64.rpm`
- RPM (Oracle Linux 8): `oracle-instantclient19.27-devel-19.27.0.0.0-1.el8.x86_64.rpm`
- RPM (Oracle Linux 7): `oracle-instantclient19.27-devel-19.27.0.0.0-1.x86_64.rpm`
- Zip file: `instantclient-sdk-linux.x64-19.27.0.0.0dbru.zip`

### For Linux for Arm (aarch64)

- RPM: `oracle-instantclient19.27-devel-19.27.0.0.0-1.el8.aarch64.rpm`
- Zip file: `instantclient-sdk-linux.arm64-19.27.0.0.0dbru.zip`

The SDK contains the following:

- Both C and C++ header files and a `makefile` for developing OCI and OCCI applications while in an Oracle Instant Client environment. Developed applications can be deployed in any client environment.
- Both C and C++ demonstration programs.
- The Object Type Translator (OTT) utility and its classes to generate application header files.
- On Linux, the `demo.mk` `makefile` is included to build demos. For example, the `instantclient_19_27` directory must be in the runtime library search path, and set LD_LIBRARY_PATH before linking the application.

**Parent topic:** [Installing Oracle Instant Client](installing-instant-client.md)
