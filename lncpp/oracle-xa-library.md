The Oracle XA library is an external interface that allows transaction managers other than the Oracle server to coordinate global transactions. The XA library supports non-Oracle resource managers in distributed transactions. This is particularly useful in transactions between several databases and resources.

The implementation of the Oracle XA library conforms to the X/Open Distributed Transaction Processing (DTP) software architecture's XA interface specification. The Oracle XA Library is installed as part of the Oracle Database Enterprise Edition.

This chapter contains these topics:

- Developing Applications with XA and OCCI

- APIs for XA Support

**See Also:**

- [`http://www.opengroup.org`](http://www.opengroup.org)

- [Oracle Database Development Guide](../adfns/xa.md) for more details on the Oracle XA library and architecture

- [OCCI Application Programming Interface](occi-application-programing-interface.md)

### 11.1 Developing Applications with XA and OCCI

For connection, disconnection, and transaction control on Oracle databases, applications must interface with a transaction manager. OCCI has APIs for interacting with `Environment` and `Connection` objects within XA and make them available for Oracle database access, such as `SELECT` queries, DML statements, object access, and so on.

Example 11-1 How to Use Transaction Managers with XA

    /* Transaction manager opens connection to the Oracle server*/
    tpopen("oracle_xa+acc=p/HR/password+sestm=10", 1, TMNOFLAGS);
    /* Transaction manager issues XA commands to start a global transaction*/
    tpbegin();

    /* Access the underlying Oracle database using OCCI */
    Environment *xaenv = Environment::getXAEnvironment(
       "oracle_xa+acc=p/HR/password+sestm=10");
    Connection *xaconn = xaenv->getXAConnection(
       "oracle_xa+acc=p/HR/password+sestm=10");

    /* Use the Environment & Connection objects */
    Statement *stmt = xaconn->createStatement(
       "Update Emp set sal = sal * 0.2");

    ...

    /* Release the Environment & Connection objects */
    xaenv->releaseXAConnection(xaconn);
    Environment::releaseXAEnvironment(xaenv);

### 11.2 APIs for XA Support

The following methods of the [Environment Class](environment-class.md) support use of XA libraries:

- [getXAConnection()](environment-class.md)

- [releaseXAEnvironment()](environment-class.md)

- [releaseXAConnection()](environment-class.md)

- [releaseXAEnvironment()](environment-class.md)

In addition, the [getXAErrorCode()](sqlexecption-class.md) method of [SQLException Class](sqlexecption-class.md) is necessary for XA enabled applications to determine if thrown exceptions are due to an SQL error (`XA_OK`) or an XA error (an XA error code).
