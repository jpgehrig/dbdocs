Lists and describes the transaction functions.

Table 26-6 lists the transaction functions that are described in this section.

Table 26-6 Transaction Functions

| Function               | Purpose                                                       |
|:-----------------------|:--------------------------------------------------------------|
| OCITransCommit()       | Commit a transaction on a service context                     |
| OCITransDetach()       | Detach a transaction from a service context                   |
| OCITransForget()       | Forget a prepared global transaction                          |
| OCITransMultiPrepare() | Prepare a transaction with multiple branches in a single cell |
| OCITransPrepare()      | Prepare a global transaction for commit                       |
| OCITransRollback()     | Roll back a transaction                                       |
| OCITransStart()        | Start a transaction on a service context                      |

### 26.7.1 OCITransCommit()

Commits the transaction associated with a specified service context.

#### Purpose

Commits the transaction associated with a specified service context.

#### Syntax

    sword OCITransCommit ( OCISvcCtx    *svchp,
                           OCIError     *errhp,
                           ub4           flags );

#### Parameters

svchp (IN)
The service context handle.

errhp (IN)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

flags (IN)
A flag used for one-phase commit optimization in global transactions.

`OCI_DEFAULT` - If the transaction is nondistributed, the flags parameter is ignored, and `OCI_DEFAULT` can be passed as its value.

`OCI_TRANS_TWOPHASE` - OCI applications managing global transactions should pass this value to the flags parameter for a two-phase commit. The default is one-phase commit.

`OCI_TRANS_WRITEIMMED` - I/O is initiated by LGWR (Log Writer Process in the background) to write the (in-memory) redo buffers to the online redo logs. `IMMEDIATE` means that the redo buffers of the transaction are written out immediately by sending a message to LGWR, which processes the message immediately.

`OCI_TRANS_WRITEBATCH` - No I/O is issued by LGWR to write the in-memory redo buffers of the transaction to the online redo logs. `BATCH` means that the LGWR batches the redo buffers before initiating I/O for the entire batch. An error occurs when you specify both `BATCH` and `IMMEDIATE`. `IMMEDIATE` is the default.

`OCI_TRANS_WRITEWAIT` - LGWR is requested to write the redo for the commit to the online redo logs, and the commit waits for the redo buffers to be written to the online redo logs. `WAIT` means that the commit does not return until the in-memory redo buffers corresponding to the transaction are written in the (persistent) online redo logs.

`OCI_TRANS_WRITENOWAIT` - LGWR is requested to write the redo for the commit to the online redo logs, but the commit returns without waiting for the buffers to be written to the online redo logs. `NOWAIT` means that the commit returns to the user before the in-memory redo buffers are flushed to the online redo logs. An error occurs when you specify both `WAIT` and `NOWAIT`. `WAIT` is the default.

**Note:**

There is a potential for silent transaction loss when you use `OCI_TRANS_WRITENOWAIT`. Transaction loss occurs silently with shutdown abort, startup force, and any instance or node failure. On an Oracle RAC system, asynchronously committed changes may not be immediately available to read on other instances.

These last four options only affect the commit of top-level nondistributed transactions and are ignored for externally coordinated distributed transactions. They can be combined using the `OR` operator, subject to the stated restrictions.

#### Comments

The transaction currently associated with the service context is committed. If it is a global transaction that the server cannot commit, this call additionally retrieves the state of the transaction from the database to be returned to the user in the error handle.

If the application has defined multiple transactions, this function operates on the transaction currently associated with the service context. If the application is working with only the implicit local transaction created when database changes are made, that implicit transaction is committed.

If the application is running in the object mode, then the modified or updated objects in the object cache for this transaction are also flushed and committed.

Under normal circumstances, `OCITransCommit()` returns with a status indicating that the transaction has either been committed or rolled back. With global transactions, it is possible that the transaction is now in doubt, meaning that it is neither committed nor terminated. In this case, `OCITransCommit()` attempts to retrieve the status of the transaction from the server. The status is returned.

#### Example

The following code example demonstrates the use of a simple local transaction, as described in "[Simple Local Transactions](managing-scalable-platforms.md)".

Using OCITransCommit() in a Simple Local Transaction

    int main()
    {
      OCIEnv *envhp;
      OCIServer *srvhp;
      OCIError *errhp;
      OCISvcCtx *svchp;
      OCIStmt *stmthp;
      void      *tmp;
      text sqlstmt[128];

      OCIEnvCreate(&envhp, OCI_DEFAULT, (void  *)0, 0, 0, 0,
            (size_t)0, (void  *)0);

      OCIHandleAlloc( (void  *) envhp, (void  **) &errhp, (ub4) OCI_HTYPE_ERROR,
                    (size_t)0, (void  **) 0);
      OCIHandleAlloc( (void  *) envhp, (void  **) &srvhp, (ub4) OCI_HTYPE_SERVER,
                    (size_t)0, (void  **) 0);

      OCIServerAttach( srvhp, errhp, (text *) 0, (sb4) 0, (ub4) OCI_DEFAULT);

      OCIHandleAlloc( (void  *) envhp, (void  **) &svchp, (ub4) OCI_HTYPE_SVCCTX,
                    (size_t)0, (void  **) 0);

      OCIHandleAlloc((void  *)envhp, (void  **)&stmthp, OCI_HTYPE_STMT, 0, 0);

      OCIAttrSet((void  *)svchp, OCI_HTYPE_SVCCTX, (void  *)srvhp, 0,
                      OCI_ATTR_SERVER, errhp);

      OCILogon(envhp, errhp, &svchp, (text *)"HR", strlen("HR"),
                     (text *)"HR", strlen("HR"), 0, 0);

      /* update hr.employees employee_id=7902, increment salary */
      sprintf((char *)sqlstmt, "UPDATE EMPLOYEES SET SALARY = SALARY + 1 \
                                                WHERE  EMPLOYEE_ID = 7902");

      OCIStmtPrepare(stmthp, errhp, sqlstmt, strlen((char *)sqlstmt),
                     OCI_NTV_SYNTAX, 0);
      OCIStmtExecute(svchp, stmthp, errhp, 1, 0, 0, 0, 0);
      OCITransCommit(svchp, errhp, (ub4) 0);

      /* update hr.employees employee_id=7902, increment salary again, but rollback */
      OCIStmtExecute(svchp, stmthp, errhp, 1, 0, 0, 0, 0);
      OCITransRollback(svchp, errhp, (ub4) 0);
    }

**Related Topics**

- OCITransRollback()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.7.2 OCITransDetach()

Detaches a global transaction.

#### Purpose

Detaches a global transaction.

#### Syntax

    sword OCITransDetach ( OCISvcCtx    *svchp,
                           OCIError     *errhp,
                           ub4           flags );

#### Parameters

svchp (IN)
The service context handle.

errhp (IN)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

flags (IN)
You must pass a value of `OCI_DEFAULT` for this parameter.

#### Comments

Detaches a global transaction from the service context handle. The transaction currently attached to the service context handle becomes inactive at the end of this call. The transaction may be resumed later by calling `OCITransStart()`, specifying a flags value of `OCI_TRANS_RESUME`.

When a transaction is detached, the value that was specified in the `timeout` parameter of `OCITransStart()` when the transaction was started is used to determine the amount of time the branch can remain inactive before being deleted by the server's `PMON` process.

**Note:**

The transaction can be resumed by a different process than the one that detached it, if the transaction has the same authorization. If this function is called before a transaction is actually started, this function has no effect.

For example code demonstrating the use of `OCITransDetach()`, see the Examples section of `OCITransStart()`.

**Related Topics**

- OCITransStart()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.7.3 OCITransForget()

Causes the server to forget a heuristically completed global transaction.

#### Purpose

Causes the server to forget a heuristically completed global transaction.

#### Syntax

    sword OCITransForget ( OCISvcCtx     *svchp,
                           OCIError      *errhp,
                           ub4            flags );

#### Parameters

svchp (IN)
The service context handle in which the transaction resides.

errhp (IN)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

flags (IN)
You must pass `OCI_DEFAULT` for this parameter.

#### Comments

Forgets a heuristically completed global transaction. The server deletes the status of the transaction from the system's pending transaction table.

You set the XID of the transaction to be forgotten as an attribute of the transaction handle (`OCI_ATTR_XID`).

**Related Topics**

- OCITransCommit()
- OCITransRollback()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.7.4 OCITransMultiPrepare()

Prepares a transaction with multiple branches in a single call.

#### Purpose

Prepares a transaction with multiple branches in a single call.

#### Syntax

    sword OCITransMultiPrepare ( OCISvcCtx    *svchp,
                                 ub4           numBranches,
                                 OCITrans    **txns,
                                 OCIError    **errhp);

#### Parameters

srvchp (IN)
The service context handle.

numBranches (IN)
The number of branches expected. It is also the array size for the next two parameters.

txns (IN)
The array of transaction handles for the branches to prepare. They should all have the `OCI_ATTR_XID` set. The global transaction ID should be the same.

errhp (IN)
The array of error handles. If `OCI_SUCCESS` is not returned, then these indicate which branches received which errors.

#### Comments

Prepares the specified global transaction for commit. This call is valid only for distributed transactions. This call is an advanced performance feature intended for use only in situations where the caller is responsible for preparing all the branches in a transaction.

**Related Topics**

- OCITransPrepare()

### 26.7.5 OCITransPrepare()

Prepares a global transaction for commit.

#### Purpose

Prepares a global transaction for commit.

#### Syntax

    sword OCITransPrepare ( OCISvcCtx    *svchp,
                            OCIError     *errhp,
                            ub4           flags );

#### Parameters

svchp (IN)
The service context handle.

errhp (IN)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

flags (IN)
You must pass `OCI_DEFAULT` for this parameter.

#### Comments

Prepares the specified global transaction for commit.

This call is valid only for global transactions.

The call returns `OCI_SUCCESS_WITH_INFO` if the transaction has not made any changes. The error handle indicates that the transaction is read-only. The `flags` parameter is not currently used.

**Related Topics**

- OCITransCommit()
- OCITransForget()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.7.6 OCITransRollback()

Rolls back the current transaction.

#### Purpose

Rolls back the current transaction.

#### Syntax

    sword OCITransRollback ( void         *svchp,
                             OCIError     *errhp,
                             ub4           flags );

#### Parameters

svchp (IN)
A service context handle. The transaction currently set in the service context handle is rolled back.

errhp (IN)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

flags (IN)
You must pass a value of `OCI_DEFAULT` for this parameter.

#### Comments

The current transaction— defined as the set of statements executed since the last `OCITransCommit()` or since `OCISessionBegin()` —is rolled back.

If the application is running under object mode, then the modified or updated objects in the object cache for this transaction are also rolled back.

Attempting to roll back a global transaction that is not currently active causes an error.

#### Examples

For example code demonstrating the use of `OCITransRollback()` see the Examples section of OCITransCommit().

**Related Topics**

- OCITransCommit()
- [OCISessionBegin()](connect-authorize-and-initialize-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.7.7 OCITransStart()

Sets the beginning of a transaction.

#### Purpose

Sets the beginning of a transaction.

#### Syntax

    sword OCITransStart ( OCISvcCtx    *svchp,
                          OCIError     *errhp,
                          uword         timeout,
                          ub4           flags );

#### Parameters

svchp (IN/OUT)
The service context handle. The transaction context in the service context handle is initialized at the end of the call if the flag specified a new transaction to be started.

errhp (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err` and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

timeout (IN)
The time, in seconds, to wait for a transaction to become available for resumption when `OCI_TRANS_RESUME` is specified. When `OCI_TRANS_NEW` is specified, the timeout parameter indicates the number of seconds the transaction can be inactive before it is automatically terminated by the system. A transaction is inactive between the time it is detached (with `OCITransDetach()`) and the time it is resumed with `OCITransStart()`.

flags (IN)
Specifies whether a new transaction is being started or an existing transaction is being resumed. Also specifies serializability or read-only status. More than a single value can be specified. By default, a read/write transaction is started. The flag values are:

- `OCI_TRANS_NEW` - Starts a new transaction branch. By default starts a tightly coupled and migratable branch.

- `OCI_TRANS_TIGHT` - Explicitly specifies a tightly coupled branch.

- `OCI_TRANS_LOOSE` - Specifies a loosely coupled branch.

- `OCI_TRANS_RESUME` - Resumes an existing transaction branch.

- `OCI_TRANS_READONLY` - Starts a read-only transaction.

- `OCI_TRANS_SERIALIZABLE` - Starts a serializable transaction.

- `OCI_TRANS_SEPARABLE` - Separates the transaction after each call.

  This flag results in a warning that the transaction was started using regular transactions. Separated transactions are not supported through release 9.0.1 of the server.

An error message results if there is an error in your code or the transaction service. The error indicates that you attempted an action on a transaction that has already been prepared.

#### Comments

This function sets the beginning of a global or serializable transaction. The transaction context currently associated with the service context handle is initialized at the end of the call if the `flags` parameter specifies that a new transaction should be started.

The XID of the transaction is set as an attribute of the transaction handle (`OCI_ATTR_XID`)

#### Examples

The following code example and the one following that one demonstrate the use of OCI transactional calls for manipulating global transactions. The concept for a single session operating on different branches, as shown in the following code example, is illustrated by [Figure 10-2](managing-scalable-platforms.md).

Using OCITransStart() in a Single Session Operating on Different Branches

    int main()
    {
      OCIEnv *envhp;
      OCIServer *srvhp;
      OCIError *errhp;
      OCISvcCtx *svchp;
      OCISession *usrhp;
      OCIStmt *stmthp1, *stmthp2;
      OCITrans *txnhp1, *txnhp2;
      void      *tmp;
      XID gxid;
      text sqlstmt[128];

      OCIEnvCreate(&envhp, OCI_DEFAULT, (void  *)0, 0, 0, 0,
            (size_t)0, (void  *)0);

      OCIHandleAlloc( (void  *) envhp, (void  **) &errhp, (ub4)
                    OCI_HTYPE_ERROR, 52, (void  **) &tmp);
      OCIHandleAlloc( (void  *) envhp, (void  **) &srvhp, (ub4)
                   OCI_HTYPE_SERVER, 52, (void  **) &tmp);

      OCIServerAttach( srvhp, errhp, (text *) 0, (sb4) 0, (ub4) OCI_DEFAULT);

      OCIHandleAlloc( (void  *) envhp, (void  **) &svchp, (ub4) OCI_HTYPE_SVCCTX,
                    52, (void  **) &tmp);

      OCIHandleAlloc((void  *)envhp, (void  **)&stmthp1, OCI_HTYPE_STMT, 0, 0);
      OCIHandleAlloc((void  *)envhp, (void  **)&stmthp2, OCI_HTYPE_STMT, 0, 0);

      OCIAttrSet((void  *)svchp, OCI_HTYPE_SVCCTX, (void  *)srvhp, 0,
                      OCI_ATTR_SERVER, errhp);

      /* set the external name and internal name in server handle */
      OCIAttrSet((void  *)srvhp, OCI_HTYPE_SERVER, (void  *) "demo", 0,
                      OCI_ATTR_EXTERNAL_NAME, errhp);
      OCIAttrSet((void  *)srvhp, OCI_HTYPE_SERVER, (void  *) "txn demo", 0,
                              OCI_ATTR_INTERNAL_NAME, errhp);

      /* allocate a user context handle */
      OCIHandleAlloc((void  *)envhp, (void  **)&usrhp, (ub4) OCI_HTYPE_SESSION,
                    (size_t) 0, (void  **) 0);

      OCIAttrSet((void  *)usrhp, (ub4)OCI_HTYPE_SESSION, (void  *)"HR",
                 (ub4)strlen("HR"), OCI_ATTR_USERNAME, errhp);
      OCIAttrSet((void  *)usrhp, (ub4)OCI_HTYPE_SESSION, (void  *)"HR",
                 (ub4)strlen("HR"),OCI_ATTR_PASSWORD, errhp);

      OCISessionBegin (svchp, errhp, usrhp, OCI_CRED_RDBMS, 0);

      OCIAttrSet((void  *)svchp, (ub4)OCI_HTYPE_SVCCTX,
                    (void  *)usrhp, (ub4)0, OCI_ATTR_SESSION, errhp);

      /* allocate transaction handle 1 and set it in the service handle */
      OCIHandleAlloc((void  *)envhp, (void  **)&txnhp1,  OCI_HTYPE_TRANS, 0, 0);
      OCIAttrSet((void  *)svchp, OCI_HTYPE_SVCCTX, (void  *)txnhp1, 0,
                              OCI_ATTR_TRANS, errhp);

      /* start a transaction with global transaction id = [1000, 123, 1] */
      gxid.formatID = 1000; /* format id = 1000 */
      gxid.gtrid_length = 3; /* gtrid = 123 */
      gxid.data[0] = 1; gxid.data[1] = 2; gxid.data[2] = 3;
      gxid.bqual_length = 1; /* bqual = 1 */
      gxid.data[3] = 1;

      OCIAttrSet((void  *)txnhp1, OCI_HTYPE_TRANS, (void  *)&gxid, sizeof(XID),
                              OCI_ATTR_XID, errhp);

      /* start global transaction 1 with 60-second time to live when detached */
      OCITransStart(svchp, errhp, 60, OCI_TRANS_NEW);

      /* update hr.employees employee_id=7902, increment salary */
      sprintf((char *)sqlstmt, "UPDATE EMPLOYEES SET SALARY = SALARY + 1 \
                                               WHERE EMPLOYEE_ID = 7902");
      OCIStmtPrepare(stmthp1, errhp, sqlstmt, strlen((char *)sqlstmt),
                     OCI_NTV_SYNTAX, 0);
      OCIStmtExecute(svchp, stmthp1, errhp, 1, 0, 0, 0, 0);

      /* detach the transaction */
      OCITransDetach(svchp, errhp, 0);

      /* allocate transaction handle 2 and set it in the service handle */
      OCIHandleAlloc((void  *)envhp, (void  **)&txnhp2,  OCI_HTYPE_TRANS, 0, 0);

      OCIAttrSet((void  *)svchp, OCI_HTYPE_SVCCTX, (void  *)txnhp2, 0,
                              OCI_ATTR_TRANS, errhp);

      /* start a transaction with global transaction id = [1000, 124, 1] */
      gxid.formatID = 1000; /* format id = 1000 */
      gxid.gtrid_length = 3; /* gtrid = 124 */
      gxid.data[0] = 1; gxid.data[1] = 2; gxid.data[2] = 4;
      gxid.bqual_length = 1; /* bqual = 1 */
      gxid.data[3] = 1;

      OCIAttrSet((void  *)txnhp2, OCI_HTYPE_TRANS, (void  *)&gxid, sizeof(XID),
                              OCI_ATTR_XID, errhp);

      /* start global transaction 2 with 90 second time to live when detached */
      OCITransStart(svchp, errhp, 90, OCI_TRANS_NEW);

      /* update hr.employees employee_id=7934, increment salary */
      sprintf((char *)sqlstmt, "UPDATE EMPLOYEES SET SALARY = SALARY + 1 \
                                                WHERE EMPLOYEE_ID = 7934");
      OCIStmtPrepare(stmthp2, errhp, sqlstmt, strlen((char *)sqlstmt),
                     OCI_NTV_SYNTAX, 0);
      OCIStmtExecute(svchp, stmthp2, errhp, 1, 0, 0, 0, 0);

      /* detach the transaction */
      OCITransDetach(svchp, errhp, 0);

      /* Resume transaction 1, increment salary and commit it */
      /* Set transaction handle 1 into the service handle */
      OCIAttrSet((void  *)svchp, OCI_HTYPE_SVCCTX, (void  *)txnhp1, 0,
                              OCI_ATTR_TRANS, errhp);

      /* attach to transaction 1, wait for 10 seconds if the transaction is busy */
      /* The wait is clearly not required in this example because no other */
      /* process/thread is using the transaction. It is only for illustration */
      OCITransStart(svchp, errhp, 10, OCI_TRANS_RESUME);
      OCIStmtExecute(svchp, stmthp1, errhp, 1, 0, 0, 0, 0);
      OCITransCommit(svchp, errhp, (ub4) 0);

      /* attach to transaction 2 and commit it */
      /* set transaction handle2 into the service handle */
      OCIAttrSet((void  *)svchp, OCI_HTYPE_SVCCTX, (void  *)txnhp2, 0,
                              OCI_ATTR_TRANS, errhp);
      OCITransCommit(svchp, errhp, (ub4) 0);
    }

Using OCITransStart() in a Single Session Operating on Multiple Branches Sharing the Same Transaction

    int main()
    {
      OCIEnv *envhp;
      OCIServer *srvhp;
      OCIError *errhp;
      OCISvcCtx *svchp;
      OCISession *usrhp;
      OCIStmt *stmthp;
      OCITrans *txnhp1, *txnhp2;
      void      *tmp;
      XID gxid;
      text sqlstmt[128];

      OCIEnvCreate(&envhp, OCI_DEFAULT, (void  *)0, 0, 0, 0,
            (size_t)0, (void  *)0);

      OCIHandleAlloc( (void  *) envhp, (void  **) &errhp, (ub4) OCI_HTYPE_ERROR,
                    52, (void  **) &tmp);
      OCIHandleAlloc( (void  *) envhp, (void  **) &srvhp, (ub4) OCI_HTYPE_SERVER,
                    52, (void  **) &tmp);

      OCIServerAttach( srvhp, errhp, (text *) 0, (sb4) 0, (ub4) OCI_DEFAULT);

      OCIHandleAlloc( (void  *) envhp, (void  **) &svchp, (ub4) OCI_HTYPE_SVCCTX,
                    52, (void  **) &tmp);

      OCIHandleAlloc((void  *)envhp, (void  **)&stmthp, OCI_HTYPE_STMT, 0, 0);

      OCIAttrSet((void  *)svchp, OCI_HTYPE_SVCCTX, (void  *)srvhp, 0,
                      OCI_ATTR_SERVER, errhp);

      /* set the external name and internal name in server handle */
      OCIAttrSet((void  *)srvhp, OCI_HTYPE_SERVER, (void  *) "demo", 0,
                      OCI_ATTR_EXTERNAL_NAME, errhp);
      OCIAttrSet((void  *)srvhp, OCI_HTYPE_SERVER, (void  *) "txn demo2", 0,
                      OCI_ATTR_INTERNAL_NAME, errhp);

      /* allocate a user context handle */
      OCIHandleAlloc((void  *)envhp, (void  **)&usrhp, (ub4) OCI_HTYPE_SESSION,
                    (size_t) 0, (void  **) 0);

      OCIAttrSet((void  *)usrhp, (ub4)OCI_HTYPE_SESSION, (void  *)"HR",
                 (ub4)strlen("HR"), OCI_ATTR_USERNAME, errhp);
      OCIAttrSet((void  *)usrhp, (ub4)OCI_HTYPE_SESSION, (void  *)"HR",
                 (ub4)strlen("HR"),OCI_ATTR_PASSWORD, errhp);

      OCISessionBegin (svchp, errhp, usrhp, OCI_CRED_RDBMS, 0);

      OCIAttrSet((void  *)svchp, (ub4)OCI_HTYPE_SVCCTX,
                    (void  *)usrhp, (ub4)0, OCI_ATTR_SESSION, errhp);

      /* allocate transaction handle 1 and set it in the service handle */
      OCIHandleAlloc((void  *)envhp, (void  **)&txnhp1,  OCI_HTYPE_TRANS, 0, 0);
      OCIAttrSet((void  *)svchp, OCI_HTYPE_SVCCTX, (void  *)txnhp1, 0,
                              OCI_ATTR_TRANS, errhp);

      /* start a transaction with global transaction id = [1000, 123, 1] */
      gxid.formatID = 1000; /* format id = 1000 */
      gxid.gtrid_length = 3; /* gtrid = 123 */
      gxid.data[0] = 1; gxid.data[1] = 2; gxid.data[2] = 3;
      gxid.bqual_length = 1; /* bqual = 1 */
      gxid.data[3] = 1;

      OCIAttrSet((void  *)txnhp1, OCI_HTYPE_TRANS, (void  *)&gxid, sizeof(XID),
                              OCI_ATTR_XID, errhp);

      /* start global transaction 1 with 60-second time to live when detached */
      OCITransStart(svchp, errhp, 60, OCI_TRANS_NEW);

      /* update hr.employees employee_id=7902, increment salary */
      sprintf((char *)sqlstmt, "UPDATE EMPLOYEES SET SALARY = SALARY + 1 \
                                                WHERE EMPLOYEE_ID = 7902");
      OCIStmtPrepare(stmthp, errhp, sqlstmt, strlen((char *)sqlstmt),
                     OCI_NTV_SYNTAX, 0);
      OCIStmtExecute(svchp, stmthp, errhp, 1, 0, 0, 0, 0);

      /* detach the transaction */
      OCITransDetach(svchp, errhp, 0);

      /* allocate transaction handle 2 and set it in the service handle */
      OCIHandleAlloc((void  *)envhp, (void  **)&txnhp2,  OCI_HTYPE_TRANS, 0, 0);
      OCIAttrSet((void  *)svchp, OCI_HTYPE_SVCCTX, (void  *)txnhp2, 0,
                              OCI_ATTR_TRANS, errhp);

      /* start a transaction with global transaction id = [1000, 123, 2] */
      /* The global transaction is tightly coupled with earlier transactions */
      /* There is not much practical value in doing this but the example */
      /* illustrates the use of tightly coupled transaction branches. */
      /* In a practical case, the second transaction that tightly couples with */
      /* the first can be executed from a different process/thread. */

      gxid.formatID = 1000; /* format id = 1000 */
      gxid.gtrid_length = 3; /* gtrid = 123 */
      gxid.data[0] = 1; gxid.data[1] = 2; gxid.data[2] = 3;
      gxid.bqual_length = 1; /* bqual = 2 */
      gxid.data[3] = 2;

      OCIAttrSet((void  *)txnhp2, OCI_HTYPE_TRANS, (void  *)&gxid,
    sizeof(XID), OCI_ATTR_XID, errhp);

      /* start global transaction 2 with 90-second time to live when detached */
      OCITransStart(svchp, errhp, 90, OCI_TRANS_NEW);

      /* update hr.employees employee_id=7902, increment salary */
      /* This is possible even if the earlier transaction has locked this row */
      /* because the two global transactions are tightly coupled */
      OCIStmtExecute(svchp, stmthp, errhp, 1, 0, 0, 0, 0);

      /* detach the transaction */
      OCITransDetach(svchp, errhp, 0);

      /* Resume transaction 1 and prepare it. This returns */
      /* OCI_SUCCESS_WITH_INFO because all branches except the last branch */
      /* are treated as read-only transactions for tightly coupled transactions */

      OCIAttrSet((void  *)svchp, OCI_HTYPE_SVCCTX, (void  *)txnhp1, 0,
                              OCI_ATTR_TRANS, errhp);
      if (OCITransPrepare(svchp, errhp, (ub4) 0) == OCI_SUCCESS_WITH_INFO)
      {
        text errbuf[512];
        ub4 buflen;
        sb4 errcode;

        OCIErrorGet ((void  *) errhp, (ub4) 1, (text *) NULL, &errcode,
        errbuf, (ub4) sizeof(errbuf), (ub4) OCI_HTYPE_ERROR);
        printf("OCITransPrepare - %s\n", errbuf);
      }

      /* attach to transaction 2 and commit it */
      /* set transaction handle2 into the service handle */
      OCIAttrSet((void  *)svchp, OCI_HTYPE_SVCCTX, (void  *)txnhp2, 0,
                              OCI_ATTR_TRANS, errhp);
      OCITransCommit(svchp, errhp, (ub4) 0);
    }

**Related Topics**

- OCITransDetach()
- [OCIErrorGet()](miscellaneous-functions.md)
