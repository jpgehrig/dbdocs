When the source and destination host are different, you must install the Oracle Database software on the destination host, so that the auxiliary instance can be created.

**Note:**

Ensure that you install the same release of Oracle Database software, with the same patch level, on both the source and destination host.

Use one of the following techniques to install the software:

- Perform a normal installation with Oracle Universal Installer (OUI).

  Install an Oracle Database whose release number is the same as that of the source database. Do not create a database; install the software only. Apply any required patches.

- Clone the source Oracle home.

  Use OUI to clone the source Oracle home. This ensures that all patches applied to the source database are present in the duplicate database.

**Parent topic:** [Preparing the Auxiliary Instance on the Destination Host](preparing-the-auxiliary-instance-destination-host.md)
