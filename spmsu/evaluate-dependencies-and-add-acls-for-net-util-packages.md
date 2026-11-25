You can receive a warning about network utility package dependencies. Use this procedure to evaluate the dependencies, and provide access by adding the appropriate access control lists (ACLs).

1.  Run the Pre-Upgrade Information Tool.

2.  Check the output from the Pre-Upgrade Information Tool (`preupgrade.jar`) for warning messages, such as the following example:

        WARNING: --> Database contains schemas with objects dependent on network packages.
        .... Refer to the Database Upgrade Guide for instructions to configure Network ACLs.
        .... USER WKSYS has dependent objects.
        .... USER SYSMAN has dependent objects.
        .... USER FLOWS_010600 has dependent objects.
        .

3.  Query the view `DBA_DEPENDENCIES` to obtain more information about the dependencies. For example:

        SELECT * FROM DBA_DEPENDENCIES
        WHERE referenced_name IN ('UTL_TCP','UTL_SMTP','UTL_MAIL','UTL_HTTP','UTL_INADDR','DBMS_LDAP')
          AND owner NOT IN ('SYS','PUBLIC','ORDPLUGINS');

4.  To ensure that the new access controls are part of your upgrade testing, prepare a post-upgrade script to make the scripts available in your database environment.

    Use the package `DBMS_NETWORK_ACL_ADMIN` to update your database access control lists (ACLs). You use this package to create, assign, and add privileges to the new access controls so that the updated access control packages can work as they did in prior releases. Refer to the example script provided in Oracle Database Real Application Security Administrator’s and Developer’s Guide to see how to use `DBMS_NETWORK_ACL_ADMIN` to update your access control list.

5.  After the upgrade, grant specific required privileges. Access is based on the usage in the original database.

**Related Topics**

- [Oracle Database Real Application Security Administrator's and Developer's Guide](../dbfsg/configuring-application-privileges-and-access-contol-lists.md)

**Parent topic:** [Pre-Upgrade Information Tool Warnings and Recommendations for Oracle Database](pre-upgrade-information-tool-warnings-and-recommendations.md)
