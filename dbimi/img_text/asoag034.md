The image displays a flowchart, which is a pictorial description of the EUS configuration process.

The flow chart starts at the top right with the question:

1.  What OID version and realm Oracle Context version do you have?

    Is it 9.2 or earlier? If true, upgrade OID or create or upgrade a realm Oracle Context in OID.

    Is it 9.0.4 or later? If true, go to Step 2.

2.  Are you using DNS Discovery?

    If no, use `NetCA` and create an `ldap.ora` file.

    If yes, go to Step 3.

3.  Optional. Use OID DAS: Set Login Name attribute, user, and group search bases for the IM Realm.

4.  Optional. Use EM: Set DB-OID authentication type for the IM Realm.

5.  Use DBCA: Register the database in the directory.

6.  Are you using the default enterprise domain?

    If no, use EM: Create a new enterprise domain in the realm and put the database into it.

    If yes, go to Step 7.

7.  Optional. Use EM: Set the user authentication type for the enterprise domain in the directory.

8.  How are users authenticated?

    If using Kerberos. use OID DAS: Set the attribute for Kerberos Principal Name in the IM realm, and the principal names for the users in the user entries in OID, then go to Step 9.

    If using password, go to Step 9.

    If using SSL, use OWM and Netmgr: Set up user and DB wallets, and configure SSL for client and DB. Next, use OWM and ODM: Set up OID wallet, and configure SSL for OID. Then go to Step 9.

9.  Use SQL: Create global schema and global roles in the database.

10. Use EM: Create user-schema mappings and enterprise roles in the directory.

11. Optional. Use EM: Add global database roles to enterprise roles in the directory.

12. Optional. Use EM: Grant enterprise roles to enterprise users in the directory.

13. Connect to the database as an enterprise user.

14. How are users authenticated?

    If using SSL or Kerberos, at the SQL prompt, use:`SQL> connect /@<set_service_name>`

    If using password, at the SQL prompt, use:`SQL> connect username/password@/<set_service_name>`

15. Configuration Finished.
