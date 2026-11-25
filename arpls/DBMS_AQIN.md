## 26  DBMS_AQIN

The `DBMS_AQIN` package plays a part in providing secure access to the Oracle JMS interfaces.

**See Also:**

[Oracle Database Advanced Queuing User's Guide ](../adque/managing-aq.md)for detailed information about `DBMS_AQIN`

This chapter contains the following topic:

- Security Model

### 26.1 DBMS_AQIN Security Model

While you should not call any subprograms in the `DBMS_AQIN` package directly, you must have the `EXECUTE` privilege on the `DBMS_AQIN` and `DBMS_AQJMS` packages to use the Oracle JMS interfaces.

Use the following syntax to accomplish this with regard to the `DBMS_AQIN` package:

    GRANT EXECUTE ON DBMS_AQIN to user;

You must have `EXECUTE` privilege on the `DBMS_AQIN` and `DBMS_AQJMS` packages to use the Oracle JMS interfaces. You can also acquire these rights through the `AQ_USER_ROLE` or the `AQ_ADMINSTRATOR_ROLE`.

**See Also:**

[Oracle Database Advanced Queuing User's Guide](../adque/index.md) for more information on accessing standard and Oracle JMS applications.
