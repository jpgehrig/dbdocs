Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleXAResource.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleXAException.md)
- [Next Class](OracleXid.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.jdbc.xa

## Class OracleXAResource

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.jdbc.xa.OracleXAResource

<!-- -->

- All Implemented Interfaces:
  [XAResource](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true)

  <!-- -->

  Direct Known Subclasses:
  [OracleXAResource](client/OracleXAResource.md)

  ------------------------------------------------------------------------



      public abstract class OracleXAResource
      extends Object
      implements XAResource

  An Oracle XA Resource.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type                                                                                                                                                                                                                                                        | Field and Description          |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------|
    | `protected `[`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)                                                                                                                                                         | `activeXid`                    |
    | `protected boolean`                                                                                                                                                                                                                                                      | `canBeMigratablySuspended`     |
    | `protected `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)                                                                                                                                                       | `connection`                   |
    | `protected `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                                                                                                                                                              | `dblink`                       |
    | `static short`                                                                                                                                                                                                                                                           | `DEFAULT_XA_TIMEOUT`           |
    | `static int`                                                                                                                                                                                                                                                             | `ORAISOLATIONMASK`             |
    | `static int`                                                                                                                                                                                                                                                             | `ORATMREADONLY`                |
    | `static int`                                                                                                                                                                                                                                                             | `ORATMREADWRITE`               |
    | `static int`                                                                                                                                                                                                                                                             | `ORATMSERIALIZABLE`            |
    | `static int`                                                                                                                                                                                                                                                             | `ORATRANSLOOSE`                |
    | `protected boolean`                                                                                                                                                                                                                                                      | `savedConnectionAutoCommit`    |
    | `protected boolean`                                                                                                                                                                                                                                                      | `savedXAConnectionAutoCommit`  |
    | `protected int`                                                                                                                                                                                                                                                          | `timeout`                      |
    | `static int`                                                                                                                                                                                                                                                             | `TMENDRSCAN`                   |
    | `static int`                                                                                                                                                                                                                                                             | `TMFAIL`                       |
    | `static int`                                                                                                                                                                                                                                                             | `TMJOIN`                       |
    | `static int`                                                                                                                                                                                                                                                             | `TMMIGRATE`                    |
    | `static int`                                                                                                                                                                                                                                                             | `TMNOFLAGS`                    |
    | `static int`                                                                                                                                                                                                                                                             | `TMNOMIGRATE`                  |
    | `static int`                                                                                                                                                                                                                                                             | `TMONEPHASE`                   |
    | `static int`                                                                                                                                                                                                                                                             | `TMPROMOTE`                    |
    | `static int`                                                                                                                                                                                                                                                             | `TMRESUME`                     |
    | `static int`                                                                                                                                                                                                                                                             | `TMSTARTRSCAN`                 |
    | `static int`                                                                                                                                                                                                                                                             | `TMSUCCESS`                    |
    | `static int`                                                                                                                                                                                                                                                             | `TMSUSPEND`                    |
    | `static int`                                                                                                                                                                                                                                                             | `XA_OK`                        |
    | `protected `[`OracleXAConnection`](OracleXAConnection.md)                                                                                                                                                                                                                | `xaconnection`                 |
    | `protected `[`Hashtable`](http://download.oracle.com/javase/8/docs/api/java/util/Hashtable.html?is-external=true)`<`[`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)`,oracle.jdbc.xa.OracleXAResource.XidListEntry>` | `xidHash`                      |

    - ### Fields inherited from interface javax.transaction.xa.[XAResource](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true)

      [`XA_RDONLY`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true#XA_RDONLY)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                              |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `OracleXAResource``()`                                                                                                                                                                                                                   |
    | `OracleXAResource``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` pm_conn, `[`OracleXAConnection`](OracleXAConnection.md)` xaconn)`<br>OracleXAResource() -- The initializer. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                                | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    |------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `protected void`                                                                                                 | `allowGlobalTxnModeOnly``(int errorCode)`                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `protected void`                                                                                                 | `checkError``(int error)`                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `protected void`                                                                                                 | `checkError``(int error, int defaultXAError)`                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `protected void`                                                                                                 | `checkError``(int error, `[`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)` sqlException)`                                                                                                                                                                                                                                                                                                                         |
    | `protected void`                                                                                                 | `checkError``(`[`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)` sqlex, int defaultXAError)`                                                                                                                                                                                                                                                                                                                       |
    | `abstract void`                                                                                                  | `commit``(`[`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)` xid, boolean onePhase)`<br>commit() -- Commit work done by global transaction specified by xid.                                                                                                                                                                                                                                                             |
    | `protected void`                                                                                                 | `createOrUpdateXid``(`[`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)` xid, boolean isSuspended, boolean[] isLocallySuspended)`<br>craeteOrUpdateXid () - Pushes the current xid.                                                                                                                                                                                                                                       |
    | `protected void`                                                                                                 | `debug``(`[`Logger`](http://download.oracle.com/javase/8/docs/api/java/util/logging/Logger.html?is-external=true)` logger, `[`Level`](http://download.oracle.com/javase/8/docs/api/java/util/logging/Level.html?is-external=true)` level, `[`Executable`](http://download.oracle.com/javase/8/docs/api/java/lang/reflect/Executable.html?is-external=true)` method, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` msg)`  |
    | `abstract void`                                                                                                  | `end``(`[`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)` xid, int flag)`<br>end()-- End work performed on behalf of a transaction branch.                                                                                                                                                                                                                                                                               |
    | `protected void`                                                                                                 | `enterGlobalTxnMode``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `protected void`                                                                                                 | `exitGlobalTxnMode``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `abstract void`                                                                                                  | `forget``(`[`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)` xid)`<br>forget() -- Tell RM to forget about a heuristically completed txn branch                                                                                                                                                                                                                                                                           |
    | `protected oracle.jdbc.internal.OracleConnection`                                                                | `getConnectionDuringExceptionHandling``()`                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `int`                                                                                                            | `getTransactionTimeout``()`<br>Obtain the current transaction timeout value set for this XAResource instance.                                                                                                                                                                                                                                                                                                                                                                |
    | `protected boolean`                                                                                              | `isOnStack``(`[`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)` xid)`                                                                                                                                                                                                                                                                                                                                                    |
    | `boolean`                                                                                                        | `isSameRM``(`[`XAResource`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true)` xares)`<br>This method is called to determine if the resource manager instance represented by the target object is the same as the resouce manager instance represented by the parameter xares.                                                                                                                                             |
    | `protected boolean`                                                                                              | `isXidListEmpty``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `protected boolean`                                                                                              | `isXidSuspended``(`[`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)` xid)`<br>isXidSuspended(Xid) - Checks if the passed Xid is suspended or not.                                                                                                                                                                                                                                                                        |
    | `abstract int`                                                                                                   | `prepare``(`[`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)` xid)`<br>prepare() -- Ask RM to prepare for a commit of the txn specified in xid.                                                                                                                                                                                                                                                                          |
    | [`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)`[]`         | `recover``(int flag)`<br>Obtain a list of prepared transaction branches from a resource manager.                                                                                                                                                                                                                                                                                                                                                                             |
    | `protected boolean`                                                                                              | `removeXidFromList``(`[`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)` xid)`                                                                                                                                                                                                                                                                                                                                            |
    | `protected void`                                                                                                 | `restoreAutoCommitModeForGlobalTransaction``()`<br>Restore the auto-commit status of the Connection & the PooledConnection.                                                                                                                                                                                                                                                                                                                                                  |
    | `protected void`                                                                                                 | `resumeStacked``(`[`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)` xid)`<br>resumeStacked() - Resumes the current transaction after the possible suspension of the stacked transaction, if any.                                                                                                                                                                                                                         |
    | `abstract void`                                                                                                  | `rollback``(`[`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)` xid)`<br>rollback() -- Ask RM to roll back work done on behalf of a txn branch.                                                                                                                                                                                                                                                                           |
    | `protected void`                                                                                                 | `saveAndAlterAutoCommitModeForGlobalTransaction``()`<br>Save the auto-commit status of the Connection & the PooledConnection.                                                                                                                                                                                                                                                                                                                                                |
    | `boolean`                                                                                                        | `setTransactionTimeout``(int seconds)`<br>Set the current transaction timeout value for this XAResource instance.                                                                                                                                                                                                                                                                                                                                                            |
    | `abstract void`                                                                                                  | `start``(`[`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)` xid, int flag)`<br>start() -- Starts work on behalf of a transaction branch.                                                                                                                                                                                                                                                                                 |
    | `protected `[`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true) | `suspendStacked``(`[`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)` xid)`<br>suspendStacked() - Suspends the stacked transaction, if any.                                                                                                                                                                                                                                                                               |
    | `protected boolean`                                                                                              | `updateXidList``(`[`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)` xid, boolean[] flags)`<br>updateXidList() - Update the Xid status in the list                                                                                                                                                                                                                                                                        |

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Field Detail

    - #### XA_OK

          public static final int XA_OK

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DEFAULT_XA_TIMEOUT

          public static final short DEFAULT_XA_TIMEOUT

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### savedConnectionAutoCommit

          protected boolean savedConnectionAutoCommit

    <!-- -->

    - #### savedXAConnectionAutoCommit

          protected boolean savedXAConnectionAutoCommit

    <!-- -->

    - #### TMNOFLAGS

          public static final int TMNOFLAGS

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### TMNOMIGRATE

          public static final int TMNOMIGRATE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### TMENDRSCAN

          public static final int TMENDRSCAN

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### TMPROMOTE

          public static final int TMPROMOTE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### TMFAIL

          public static final int TMFAIL

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### TMMIGRATE

          public static final int TMMIGRATE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### TMJOIN

          public static final int TMJOIN

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### TMONEPHASE

          public static final int TMONEPHASE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### TMRESUME

          public static final int TMRESUME

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### TMSTARTRSCAN

          public static final int TMSTARTRSCAN

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### TMSUCCESS

          public static final int TMSUCCESS

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### TMSUSPEND

          public static final int TMSUSPEND

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ORATMREADONLY

          public static final int ORATMREADONLY

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ORATMREADWRITE

          public static final int ORATMREADWRITE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ORATMSERIALIZABLE

          public static final int ORATMSERIALIZABLE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ORAISOLATIONMASK

          public static final int ORAISOLATIONMASK

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ORATRANSLOOSE

          public static final int ORATRANSLOOSE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### connection

          protected Connection connection

    <!-- -->

    - #### xaconnection

          protected OracleXAConnection xaconnection

    <!-- -->

    - #### timeout

          protected int timeout

    <!-- -->

    - #### dblink

          protected String dblink

    <!-- -->

    - #### canBeMigratablySuspended

          protected boolean canBeMigratablySuspended

    <!-- -->

    - #### activeXid

          protected Xid activeXid

    <!-- -->

    - #### xidHash

          protected Hashtable<Xid,oracle.jdbc.xa.OracleXAResource.XidListEntry> xidHash

  <!-- -->

  - ### Constructor Detail

    - #### OracleXAResource

          public OracleXAResource()

    <!-- -->

    - #### OracleXAResource

          public OracleXAResource(Connection pm_conn,
                                  OracleXAConnection xaconn)
                           throws XAException

      OracleXAResource() -- The initializer.
      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true) - throws an exception if the connection object is null.

  <!-- -->

  - ### Method Detail

    - #### removeXidFromList

          protected final boolean removeXidFromList(Xid xid)

    <!-- -->

    - #### isOnStack

          protected final boolean isOnStack(Xid xid)
                                     throws XAException

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true)

    <!-- -->

    - #### isXidListEmpty

          protected final boolean isXidListEmpty()

    <!-- -->

    - #### createOrUpdateXid

          protected void createOrUpdateXid(Xid xid,
                                           boolean isSuspended,
                                           boolean[] isLocallySuspended)

      craeteOrUpdateXid () - Pushes the current xid. This should be called from start.
      Parameters:
      `xid` - Xid to save.

    <!-- -->

    - #### updateXidList

          protected boolean updateXidList(Xid xid,
                                          boolean[] flags)

      updateXidList() - Update the Xid status in the list
      Returns:
      true - if the xid is found the xidlist false - if the xid is not found the xidlist

    <!-- -->

    - #### isXidSuspended

          protected boolean isXidSuspended(Xid xid)
                                    throws XAException

      isXidSuspended(Xid) - Checks if the passed Xid is suspended or not.
      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true) - if the suspend operation fails.

    <!-- -->

    - #### suspendStacked

          protected Xid suspendStacked(Xid xid)
                                throws XAException

      suspendStacked() - Suspends the stacked transaction, if any. This version should be called at the beginning of commit, rollback, and prepare.
      Parameters:
      `xid` - Xid of current transaction. If this is different from the stacked Xid, the stacked Xid will be suspended, clearing the way for the current operation.

      Returns:
      null if there was no stacked Xid, otherwise the Xid which was stacked.

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true) - if the suspend operation fails.

    <!-- -->

    - #### resumeStacked

          protected void resumeStacked(Xid xid)
                                throws XAException

      resumeStacked() - Resumes the current transaction after the possible suspension of the stacked transaction, if any. This should be called from the end of commit, rollback, prepare, and end.
      Parameters:
      `xid` - Xid of stacked transaction. If null, then this is a no-op.

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true) - if the resume operation fails.

    <!-- -->

    - #### start

          public abstract void start(Xid xid,
                                     int flag)
                              throws XAException

      start() -- Starts work on behalf of a transaction branch. If TMJOIN is specified, the start is for joining an exisiting txn branch xid. If TMRESUME is specified, the start is to resume a suspended transaction branch specified in xid. Transaction suspend is done by calling the end method specifying the TMSUSPEND flag. If neither TMJOIN nor TMRESUME is specified and the transaction branch specified in xid already exists, the resource manager raises the duplicate transaction exception via XAER_DUPID.
      Specified by:
      [`start`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true#start_javax_transaction_xa_Xid_int_) in interface [`XAResource`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true)

      Parameters:
      `xid` - A global transaction identifier.

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true) - An error has occurred. Possible exceptions are XA_RB, XAER_RMERR, XAER_RMFAIL, XAER_DUPID, XAER_OUTSIDE, XAER_NOTA, XAER_INVAL, or XAER_PROTO.

    <!-- -->

    - #### end

          public abstract void end(Xid xid,
                                   int flag)
                            throws XAException

      end()-- End work performed on behalf of a transaction branch. The resource manager dissociates the XA resource from the transaction branch specified and let the transaction be completed. If TMSUSPEND is specified in flag, the txn branch is temporarily suspended in incomplete state. The txn context is in suspened state and must be resumed via start with TMRESUME specified. If TMFAIL is specified, the portion of work has failed. The RM may mark the transaction as rollback-only. If TMSUCCESS is specified, the portion of work has completed successfully.
      Specified by:
      [`end`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true#end_javax_transaction_xa_Xid_int_) in interface [`XAResource`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true)

      Parameters:
      `xid` - A global transaction identifier that is the same as what was used previously in the start method.

      `flag` - One of TMSUCCESS, TMFAIL, or TMSUSPEND.

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true) - An error has occurred. Possible XAException values are XAER_RMERR, XAER_RMFAILED, XAER_NOTA, XAER_INVAL, XAER_PROTO, or XA_RB.

    <!-- -->

    - #### commit

          public abstract void commit(Xid xid,
                                      boolean onePhase)
                               throws XAException

      commit() -- Commit work done by global transaction specified by xid.
      Specified by:
      [`commit`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true#commit_javax_transaction_xa_Xid_boolean_) in interface [`XAResource`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true)

      Parameters:
      `xid` - A global transaction identifier.

      `onePhase` - If true, the RM should use a 1-phase commit protocol to commit the work done on behalf of xid.

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true) - (An error has occurred.) Possible XAExceptions are XA_HEURHAZ, XA_HEURCOM, XA_HEURRB, XA_HEURMIX, XAER_RMERR, XAER_RMFAIL, XAER_NOTA, XAER_INVAL, or XAER_PROTO. If the resource manager did not commit the txn and the paramether onePhase is set to true, the RM may raise one of the XA_RB exceptions. Upon return, the RM has rolled back the branch's work and has released all held resources.

    <!-- -->

    - #### prepare

          public abstract int prepare(Xid xid)
                               throws XAException

      prepare() -- Ask RM to prepare for a commit of the txn specified in xid.
      Specified by:
      [`prepare`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true#prepare_javax_transaction_xa_Xid_) in interface [`XAResource`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true)

      Parameters:
      `xid` - A global transaction identifier.

      Returns:
      A value indicating the resource manager's vote on the outcome of the txn. The possible values are: XA_RDONLY or XA_OK. If the RM wants to roll back the transaction, it should do so by raising an appropriate XAException in the prepare method.

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true) - (An error has occurred.) Possible exception values are: XA_RB, XAER_RMERR, XAER_RMFAIL, XAER_NOTA, XAER_INVAL, or XAER_PROTO.

    <!-- -->

    - #### forget

          public abstract void forget(Xid xid)
                               throws XAException

      forget() -- Tell RM to forget about a heuristically completed txn branch
      Specified by:
      [`forget`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true#forget_javax_transaction_xa_Xid_) in interface [`XAResource`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true)

      Parameters:
      `xid` - A global transaction identifier.

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true) - An error has occurred. Possible exception values are XAER_RMERR, XAER_RMFAIL, XAER_NOTA, XAER_INVAL, or XAER_PROTO.

    <!-- -->

    - #### rollback

          public abstract void rollback(Xid xid)
                                 throws XAException

      rollback() -- Ask RM to roll back work done on behalf of a txn branch.
      Specified by:
      [`rollback`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true#rollback_javax_transaction_xa_Xid_) in interface [`XAResource`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true)

      Parameters:
      `xid` - A global transaction identifier.

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true) - An error has occurred.

    <!-- -->

    - #### recover

          public Xid[] recover(int flag)
                        throws XAException

      Obtain a list of prepared transaction branches from a resource manager. The transaction manager calls this method during recovery to obtain the list of transaction branches that are currently in prepared or heuristically completed states. JDBC has been returning a complete list of prepared transaction branches when recover(flag) is called regardless which flag (TMNOFLAGS or TMSTARTRSCAN or TMENDRSCAN) is set. Beginning in 11.2.0.2, JDBC will do the following in order to accommodate certain TMs way of handling the recovery scan:
      - If recover(TMSTARTRSCAN) is called, continues to return a complete list of prepared transaction branches.
      - If recover(TMNOFLAGS) is called after a TMSTARTSCAN, returns an empty list until the scan is ended. Otherwise, continues to return a complete list of prepared transaction branches.
      - If recover(TMENDRSCAN) is called after a TMSTARTSCAN, ends the scan and returns an empty list. Otherwise, continues to return a complete list of prepared transaction branches until TMSTARTRSCAN is called again.

      ### Example 1:

                MyXid[] xids =
                   xaRes.recover(XAResource.TMSTARTRSCAN | XAResource.TMENDRSCAN);
                for (int i=0; xids != null && i < xids.length; i++) {
                try {
                   xaRes.rollback(xids[i]);
                ...


      ### Example 2:

                MyXid[] xids = xaRes.recover(XAResource.TMSTARTRSCAN);
                while( xids!=null && xids.length>0)
                {
                   for (int i=0; i < xids.length; i++) {
                   try {
                      xaRes.rollback(xids[i]);
                      ...
                      xids = xaRes.recover(XAResource.TMNOFLAG);
                }
                xaRes.recover(XAResource.TMENDRSCAN);


      ### Example 3:

                MyXid[] xids = xaRes.recover(XAResource.TMNOFLAG);
                for (int i=0; xids != null && i < xids.length; i++) {
                try {
                   xaRes.rollback(xids[i]);
                ...


      Specified by:
      [`recover`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true#recover_int_) in interface [`XAResource`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true)

      Parameters:
      `flag` - One of TMSTARTRSCAN, TMENDRSCAN, TMNOFLAGS. TMNOFLAGS must be used when no other flags are set in flags.

      Returns:
      The resource manager returns zero or more XIDs for the transaction branches that are currently in a prepared or heuristically completed state. If an error occurs during the operation, the resource manager should raise the appropriate XAException.

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true) - An error has occurred. Possible values are XAER_RMERR, XAER_RMFAIL, XAER_INVAL, and XAER_PROTO.

    <!-- -->

    - #### restoreAutoCommitModeForGlobalTransaction

          protected void restoreAutoCommitModeForGlobalTransaction()
                                                            throws XAException

      Restore the auto-commit status of the Connection & the PooledConnection. Typically invoked after the end of a global transaction.
      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true)

    <!-- -->

    - #### saveAndAlterAutoCommitModeForGlobalTransaction

          protected void saveAndAlterAutoCommitModeForGlobalTransaction()
                                                                 throws XAException

      Save the auto-commit status of the Connection & the PooledConnection. Typically invoked just before starting the transaction.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true)

    <!-- -->

    - #### getTransactionTimeout

          public int getTransactionTimeout()
                                    throws XAException

      Obtain the current transaction timeout value set for this XAResource instance. If XAResource.setTransactionTimeout was not use prior to invoking this method, the return value is the default timeout set fo the resource manager; otherwise, the value used in the previous setTransactionTimeout call is returned.
      Specified by:
      [`getTransactionTimeout`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true#getTransactionTimeout__) in interface [`XAResource`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true)

      Returns:
      the transaction timeout value in seconds.

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true) - - An error has occurred. Possible exception values are XAER_RMERR, XAER_RMFAIL.

    <!-- -->

    - #### isSameRM

          public boolean isSameRM(XAResource xares)
                           throws XAException

      This method is called to determine if the resource manager instance represented by the target object is the same as the resouce manager instance represented by the parameter xares.
      Specified by:
      [`isSameRM`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true#isSameRM_javax_transaction_xa_XAResource_) in interface [`XAResource`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true)

      Parameters:
      `xares` - - An XAResource object whose resource manager instance is to be compared with the resource manager instance of the target object.

      Returns:
      true if it's the same RM instance; otherwise false.

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true) - - An error has occurred. Possible exception values are XAER_RMERR, XAER_RMFAIL.

    <!-- -->

    - #### setTransactionTimeout

          public boolean setTransactionTimeout(int seconds)
                                        throws XAException

      Set the current transaction timeout value for this XAResource instance. Once set, this timeout value is effective until setTransactionTimeout is invoked again with a different value. To reset the timeout value to the default value used by the resource manager, set the value to zero. If the timeout operation is performed successfully, the method returns true; otherwise false. If a resource manager does not support transaction timeout value to be set explicitly, this method returns false.
      Specified by:
      [`setTransactionTimeout`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true#setTransactionTimeout_int_) in interface [`XAResource`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true)

      Parameters:
      `seconds` - - transaction timeout value in seconds.

      Returns:
      true if transaction timeout value is set successfully; otherwise false.

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true) - - An error has occurred. Possible exception values are XAER_RMERR, XAER_RMFAIL, or XAER_INVAL.

    <!-- -->

    - #### allowGlobalTxnModeOnly

          protected void allowGlobalTxnModeOnly(int errorCode)
                                         throws XAException

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true)

    <!-- -->

    - #### exitGlobalTxnMode

          protected void exitGlobalTxnMode()

    <!-- -->

    - #### enterGlobalTxnMode

          protected void enterGlobalTxnMode()

    <!-- -->

    - #### checkError

          protected void checkError(int error)
                             throws XAException

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true)

    <!-- -->

    - #### checkError

          protected void checkError(int error,
                                    SQLException sqlException)
                             throws XAException

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true)

    <!-- -->

    - #### checkError

          protected void checkError(int error,
                                    int defaultXAError)
                             throws XAException

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true)

    <!-- -->

    - #### checkError

          protected void checkError(SQLException sqlex,
                                    int defaultXAError)
                             throws XAException

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true)

    <!-- -->

    - #### getConnectionDuringExceptionHandling

          protected oracle.jdbc.internal.OracleConnection getConnectionDuringExceptionHandling()

    <!-- -->

    - #### debug

          protected void debug(Logger logger,
                               Level level,
                               Executable method,
                               String msg)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleXAResource.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleXAException.md)
- [Next Class](OracleXid.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Copyright © 2008, 2022, Oracle and/or its affiliates.
