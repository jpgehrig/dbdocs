# Description of the illustration dbseg_vm_004.png

Figure dbseg_vm_004.png illustrates the environment in which you can audit proxy users. In this figure, from left to right, top to bottom, are the following components:

- A client connects to a mid-tier application called AppHR.

- The apphr mid-tier application passes the user's authentication to the database server.

- Within the database is the audit trail. To find information about this user's activities, you can query the following columns from the UNIFIED_AUDIT_TRAIL data dictionary view:

  - UNIFIED_AUDIT_TRAIL.DBPROXY_USERNAME = 'apphr' (Proxy user for user jackson)

  - UNIFIED_AUDIT_TRAIL.PROXY_SESSIONID = 3205062574 (ID for the apphr proxy user login)

  - UNIFIED_AUDIT_TRAIL.ACTION_NAME = 'CREATE TABLE' (User jackson's actions)
