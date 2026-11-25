Java Virtual Machine fully supports the family of Java Standard Edition `java.lang.Runtime.exec` methods. These methods spawn a new operating system (OS) process to run a user-supplied command. On the server, you must use these methods with caution. In Java Virtual Machine, OS command execution permissions are not granted to all database users by default and are issued only by privileged administrators. If you are a DBA, then you must know how to use the `Runtime.exec` functionality in Oracle Database and follow the recommendations. Also, you must be selective about issuing these permissions to database users.

**Related Topics**

- [Secure Use of Runtime.exec Functionality in Oracle Database](Runtime-exe-secure-use.md)
