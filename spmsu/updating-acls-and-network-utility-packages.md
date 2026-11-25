Use this procedure to update access control lists (ACLs) and Network Utility Packages.

Starting with Oracle Database 12c, the access control of the UTL packages is implemented using Oracle Database Real Application Security. UTL packages include UTL_TCP, UTL_SMTP, UTL_MAIL, UTL_HTTP, and UTL_INADDR. The access control does not require Oracle XML DB.

1.  Ensure that the logged-in user has the `connect` privilege for the host and port specified by `DBMS_LDAP.init`. There is new behavior for the `DBMS_LDAP` PL/SQL package and the `HttpUriType` type. Because of this new behavior, you must create or update access control lists (ACLs) after you upgrade to the new Oracle Database release.

    For example, if your application depends on the `DBMS_LDAP` package, then the error "ORA-24247: network access denied by access control list (ACL)" can occur. To avoid this error, the logged-in user must have the `connect` privilege for the host and port specified by `DBMS_LDAP.init`.

2.  If you have any of the following packages installed, then you can be required to reinstall these packages after upgrade:

    - `UTL_TCP`

    - `UTL_SMTP`

    - `UTL_MAIL`

    - `UTL_HTTP`

    - `UTL_INADDR`

    Ensure that you have the latest version of these packages for the new Oracle Database release.

**See Also:**

[Oracle Database Real Application Security Administrator's and Developer's Guide](../dbfsg/configuring-application-privileges-and-access-contol-lists.md) for information about configuring access control lists

**Parent topic:** [Pre-Upgrade Information Tool Warnings and Recommendations for Oracle Database](pre-upgrade-information-tool-warnings-and-recommendations.md)
