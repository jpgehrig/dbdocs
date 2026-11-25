# Description of the illustration dvadm_vm_004b.png

This figure illustrates how realm authorization works for two realm owners, the Order Entry realm owner and the Human Resources realm owner. The Order Entry realm owner has the OE_ADMIN role, and the Human Resources realm own has HR_ADMIN role. Both of these realm owners have the following database privileges:

- CREATE ANY TABLE

- DROP ANY TABLE

- SELECT ANY TABLE

- GRANT/REVOKE

When these realm owners perform an action in their respective schemas—OE schema for the Order Entry realm owner and the HR schema for the Human Resources realm owner—the Oracle Database Vault realm authorizations allow them to perform any of the database privileges to which they are assigned.

However, they are not permitted to perform these actions in each other's realm. For example, the Order Entry realm owner cannot create tables in the HR schema, nor can the Human Resource realm owner drop tables from the OE schema.
