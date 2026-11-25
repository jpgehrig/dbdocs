# Description of the illustration dvadm_vm_003.png

dvadm_vm_008.png has the following components, left to right:

- A database containing PL/SQL metadata and the finance.vendors table. This data is blocked from database administrators because it is protected by a realm.

- To right of the database, the DBA attempts a query, SELECT \* FROM FINANCE.VENDORS, even though he has the SELECT ANY TABLE privilege. However, Oracle Database Vault realm for this table prevents the DBA from accessing this data.
