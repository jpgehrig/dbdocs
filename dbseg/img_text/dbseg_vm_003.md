# Description of the illustration dbseg_vm_003.png

Figure dbseg_vm0_03.png illustrates an environment in which you can audit the client identifier of a user. From left to right, top to bottom, top to bottom, are the following components:

- A client connects to a mid-tier application called AppInventory.

- The AppInventory mid-tier application passes the user's authentication to the first database, Database 1. The AppInventory application sets the client identifier to CLIENT_A.

- From Database 1, you can audit the client identifier CLIENT_A by querying the CLIENT_IDENTIFIER column of the UNIFIED_AUDIT_TRAIL view.

- A database link connects Database 1 to a second database, Database 2. The user now has connected to Database 2.

- From Database 2, you can audit the client identifer again, by querying the CLIENT_ID column of the UNIFIED_AUDIT_TRAIL view.
