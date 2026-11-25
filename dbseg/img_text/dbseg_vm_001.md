# Description of the illustration dbseg_vm_001.png

Figure dbseg_vm_001.png illustrates how connections work. From left to right, top to bottom, are the following components:

- Unpatched Oracle 9i client (U), which tries to use the Oracle Net Services protocol negotiation to connect to a fixed host Oracle Database link (H). It fails. The fixed Oracle Database link, for Oracle Database 12c, connects to an Oracle 9i target (T).

- 10g Client (E), which can connect because it has had the critical patch update CPUOct2012 applied.

- Following the 9i client is an Oracle Database Release 11.2.0.3 client (C), which succeeds in using the Oracle Net Services protocol to connect first to the fixed host database link (H), and then to the target Oracle 9i database (T).

- The SQLNET.ALLOWED_LOGON settings for the host and target databases are as follows:

  - Fixed host 12c (H) is set as as follows:

    H acts as a client to T by using SQLNET.ALLOWED_LOGON_VERSION_CLIENT=8

    H also acts as the server for (C) and (U) by using SQLNET.ALLOWED_LOGON_VERSION_SERVER=12

  - Target 9i database (T) is set to SQLNET.ALLOWED_LOGON_VERSION = 8
