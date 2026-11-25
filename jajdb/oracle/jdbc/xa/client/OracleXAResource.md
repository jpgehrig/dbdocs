Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleXAResource.md)
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleXAHeteroResource.md)
- Next Class

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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

oracle.jdbc.xa.client

## Class OracleXAResource

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.jdbc.xa.OracleXAResource](../OracleXAResource.md)

  - - oracle.jdbc.xa.client.OracleXAResource

<!-- -->

- All Implemented Interfaces:
  [XAResource](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true)

  <!-- -->

  Direct Known Subclasses:
  [OracleXAHeteroResource](OracleXAHeteroResource.md)

  ------------------------------------------------------------------------



      public class OracleXAResource
      extends OracleXAResource

  Implements javax.transaction.xa.XAResource.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from class oracle.jdbc.xa.[OracleXAResource](../OracleXAResource.md)

      [`activeXid`](../OracleXAResource.md)`, `[`canBeMigratablySuspended`](../OracleXAResource.md)`, `[`connection`](../OracleXAResource.md)`, `[`dblink`](../OracleXAResource.md)`, `[`DEFAULT_XA_TIMEOUT`](../OracleXAResource.md)`, `[`ORAISOLATIONMASK`](../OracleXAResource.md)`, `[`ORATMREADONLY`](../OracleXAResource.md)`, `[`ORATMREADWRITE`](../OracleXAResource.md)`, `[`ORATMSERIALIZABLE`](../OracleXAResource.md)`, `[`ORATRANSLOOSE`](../OracleXAResource.md)`, `[`savedConnectionAutoCommit`](../OracleXAResource.md)`, `[`savedXAConnectionAutoCommit`](../OracleXAResource.md)`, `[`timeout`](../OracleXAResource.md)`, `[`TMENDRSCAN`](../OracleXAResource.md)`, `[`TMFAIL`](../OracleXAResource.md)`, `[`TMJOIN`](../OracleXAResource.md)`, `[`TMMIGRATE`](../OracleXAResource.md)`, `[`TMNOFLAGS`](../OracleXAResource.md)`, `[`TMNOMIGRATE`](../OracleXAResource.md)`, `[`TMONEPHASE`](../OracleXAResource.md)`, `[`TMPROMOTE`](../OracleXAResource.md)`, `[`TMRESUME`](../OracleXAResource.md)`, `[`TMSTARTRSCAN`](../OracleXAResource.md)`, `[`TMSUCCESS`](../OracleXAResource.md)`, `[`TMSUSPEND`](../OracleXAResource.md)`, `[`XA_OK`](../OracleXAResource.md)`, `[`xaconnection`](../OracleXAResource.md)`, `[`xidHash`](../OracleXAResource.md)

    <!-- -->

    - ### Fields inherited from interface javax.transaction.xa.[XAResource](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true)

      [`XA_RDONLY`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true#XA_RDONLY)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                        |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `OracleXAResource``()`                                                                                                                                                                             |
    | `OracleXAResource``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` pm_conn, `[`OracleXAConnection`](../OracleXAConnection.md)` xaconn)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                      |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `commit``(`[`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)` xid, boolean onePhase)`<br>commit() -- Commit work done by global transaction specified by xid.                                                            |
    | `protected void`  | `doCommit``(`[`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)` xid, boolean onePhase)`                                                                                                                                  |
    | `protected int`   | `doDoTwoPhaseAction``(int nsites, int action, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[] dbnames, `[`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)`[] xids)`  |
    | `protected int`   | `doEnd``(`[`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)` xid, int flag, boolean isLocallySuspended)`                                                                                                                 |
    | `protected int`   | `doForget``(`[`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)` xid)`                                                                                                                                                    |
    | `protected int`   | `doPrepare``(`[`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)` xid)`                                                                                                                                                   |
    | `protected void`  | `doRollback``(`[`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)` xid)`                                                                                                                                                  |
    | `protected int`   | `doStart``(`[`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)` xid, int flag)`                                                                                                                                           |
    | `void`            | `doTwoPhaseAction``(int nsites, int action, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[] dbnames, `[`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)`[] xids)`    |
    | `void`            | `end``(`[`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)` xid, int flag)`<br>end()-- End work performed on behalf of a transaction branch.                                                                              |
    | `void`            | `forget``(`[`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)` xid)`<br>forget() -- Tell RM to forget about a heuristically completed txn branch                                                                          |
    | `int`             | `prepare``(`[`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)` xid)`<br>prepare() -- Ask RM to prepare for a commit of the txn specified in xid.                                                                         |
    | `void`            | `rollback``(`[`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)` xid)`<br>rollback() -- Ask RM to roll back work done on behalf of a txn branch.                                                                          |
    | `void`            | `start``(`[`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)` xid, int flag)`<br>start() -- Starts work on behalf of a transaction branch.                                                                                |

    - ### Methods inherited from class oracle.jdbc.xa.[OracleXAResource](../OracleXAResource.md)

      [`allowGlobalTxnModeOnly`](../OracleXAResource.md)`, `[`checkError`](../OracleXAResource.md)`, `[`checkError`](../OracleXAResource.md)`, `[`checkError`](../OracleXAResource.md)`, `[`checkError`](../OracleXAResource.md)`, `[`createOrUpdateXid`](../OracleXAResource.md)`, `[`debug`](../OracleXAResource.md)`, `[`enterGlobalTxnMode`](../OracleXAResource.md)`, `[`exitGlobalTxnMode`](../OracleXAResource.md)`, `[`getConnectionDuringExceptionHandling`](../OracleXAResource.md)`, `[`getTransactionTimeout`](../OracleXAResource.md)`, `[`isOnStack`](../OracleXAResource.md)`, `[`isSameRM`](../OracleXAResource.md)`, `[`isXidListEmpty`](../OracleXAResource.md)`, `[`isXidSuspended`](../OracleXAResource.md)`, `[`recover`](../OracleXAResource.md)`, `[`removeXidFromList`](../OracleXAResource.md)`, `[`restoreAutoCommitModeForGlobalTransaction`](../OracleXAResource.md)`, `[`resumeStacked`](../OracleXAResource.md)`, `[`saveAndAlterAutoCommitModeForGlobalTransaction`](../OracleXAResource.md)`, `[`setTransactionTimeout`](../OracleXAResource.md)`, `[`suspendStacked`](../OracleXAResource.md)`, `[`updateXidList`](../OracleXAResource.md)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Constructor Detail

    - #### OracleXAResource

          public OracleXAResource()

    <!-- -->

    - #### OracleXAResource

          public OracleXAResource(Connection pm_conn,
                                  OracleXAConnection xaconn)
                           throws XAException

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true)

  <!-- -->

  - ### Method Detail

    - #### start

          public void start(Xid xid,
                            int flag)
                     throws XAException

      start() -- Starts work on behalf of a transaction branch. If TMJOIN is specified, the start is for joining an exisiting txn branch xid. If TMRESUME is specified, the start is to resume a suspended transaction branch specified in xid. Transaction suspend is done by calling the end method specifying the TMSUSPEND flag. If neither TMJOIN nor TMRESUME is specified and the transaction branch specified in xid already exists, the resource manager raises the duplicate transaction exception via XAER_DUPID. start() allows Isolation flags to be set, only when beginning a new transaction. XAER_INVAL exception is raised for error cases, such as (1) when JOIN/RESUME specified on start (2) invalid Isol flag is set. The valid Isolation levels allowed are: ORATMREADONLY ORATMREADWRITE ORATMSERIALIZABLE
      Specified by:
      [`start`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true#start_javax_transaction_xa_Xid_int_) in interface [`XAResource`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true)

      Specified by:
      [`start`](../OracleXAResource.md) in class [`OracleXAResource`](../OracleXAResource.md)

      Parameters:
      `xid` - A global transaction identifier.

      `flag` - One of TMNOFLAGS, TMJOIN, TMNOMIGRATE or TMRESUME.

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true) - An error has occurred. Possible exceptions are XA_RB, XAER_RMERR, XAER_RMFAIL, XAER_DUPID, XAER_OUTSIDE, XAER_NOTA, XAER_INVAL, or XAER_PROTO.

    <!-- -->

    - #### doStart

          protected int doStart(Xid xid,
                                int flag)
                         throws XAException,
                                SQLException

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true)

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### end

          public void end(Xid xid,
                          int flag)
                   throws XAException

      end()-- End work performed on behalf of a transaction branch. The resource manager dissociates the XA resource from the transaction branch specified and let the transaction be completed. If TMSUSPEND is specified in flag, the txn branch is temporarily suspended in incomplete state. The txn context is in suspened state and must be resumed via start with TMRESUME specified. If TMFAIL is specified, the portion of work has failed. The RM may mark the transaction as rollback-only. If TMSUCCESS is specified, the portion of work has completed successfully.
      Specified by:
      [`end`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true#end_javax_transaction_xa_Xid_int_) in interface [`XAResource`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true)

      Specified by:
      [`end`](../OracleXAResource.md) in class [`OracleXAResource`](../OracleXAResource.md)

      Parameters:
      `xid` - A global transaction identifier that is the same as what was used previously in the start method.

      `flag` - One of TMSUCCESS, TMFAIL, or TMSUSPEND.

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true) - An error has occurred. Possible XAException values are XAER_RMERR, XAER_RMFAILED, XAER_NOTA, XAER_INVAL, XAER_PROTO, or XA_RB.

    <!-- -->

    - #### doEnd

          protected int doEnd(Xid xid,
                              int flag,
                              boolean isLocallySuspended)
                       throws XAException,
                              SQLException

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true)

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### commit

          public void commit(Xid xid,
                             boolean onePhase)
                      throws XAException

      commit() -- Commit work done by global transaction specified by xid.
      Specified by:
      [`commit`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true#commit_javax_transaction_xa_Xid_boolean_) in interface [`XAResource`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true)

      Specified by:
      [`commit`](../OracleXAResource.md) in class [`OracleXAResource`](../OracleXAResource.md)

      Parameters:
      `xid` - A global transaction identifier.

      `onePhase` - If true, the RM should use a 1-phase commit protocol to commit the work done on behalf of xid.

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true) - (An error has occurred.) Possible XAExceptions are XA_HEURHAZ, XA_HEURCOM, XA_HEURRB, XA_HEURMIX, XAER_RMERR, XAER_RMFAIL, XAER_NOTA, XAER_INVAL, or XAER_PROTO. If the resource manager did not commit the txn and the paramether onePhase is set to true, the RM may raise one of the XA_RB exceptions. Upon return, the RM has rolled back the branch's work and has released all held resources.

    <!-- -->

    - #### doCommit

          protected void doCommit(Xid xid,
                                  boolean onePhase)
                           throws XAException,
                                  SQLException

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true)

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### prepare

          public int prepare(Xid xid)
                      throws XAException

      prepare() -- Ask RM to prepare for a commit of the txn specified in xid.
      Specified by:
      [`prepare`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true#prepare_javax_transaction_xa_Xid_) in interface [`XAResource`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true)

      Specified by:
      [`prepare`](../OracleXAResource.md) in class [`OracleXAResource`](../OracleXAResource.md)

      Parameters:
      `xid` - A global transaction identifier.

      Returns:
      A value indicating the resource manager's vote on the outcome of the txn. The possible values are: XA_RDONLY or XA_OK. If the RM wants to roll back the transaction, it should do so by raising an appropriate XAException in the prepare method.

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true) - (An error has occurred.) Possible exception values are: XA_RB, XAER_RMERR, XAER_RMFAIL, XAER_NOTA, XAER_INVAL, or XAER_PROTO.

    <!-- -->

    - #### doPrepare

          protected int doPrepare(Xid xid)
                           throws XAException,
                                  SQLException

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true)

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### forget

          public void forget(Xid xid)
                      throws XAException

      forget() -- Tell RM to forget about a heuristically completed txn branch
      Specified by:
      [`forget`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true#forget_javax_transaction_xa_Xid_) in interface [`XAResource`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true)

      Specified by:
      [`forget`](../OracleXAResource.md) in class [`OracleXAResource`](../OracleXAResource.md)

      Parameters:
      `xid` - A global transaction identifier.

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true) - An error has occurred. Possible exception values are XAER_RMERR, XAER_RMFAIL, XAER_NOTA, XAER_INVAL, or XAER_PROTO.

    <!-- -->

    - #### doForget

          protected int doForget(Xid xid)
                          throws XAException,
                                 SQLException

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true)

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### rollback

          public void rollback(Xid xid)
                        throws XAException

      rollback() -- Ask RM to roll back work done on behalf of a txn branch.
      Specified by:
      [`rollback`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true#rollback_javax_transaction_xa_Xid_) in interface [`XAResource`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true)

      Specified by:
      [`rollback`](../OracleXAResource.md) in class [`OracleXAResource`](../OracleXAResource.md)

      Parameters:
      `xid` - A global transaction identifier.

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true) - An error has occurred.

    <!-- -->

    - #### doRollback

          protected void doRollback(Xid xid)
                             throws XAException,
                                    SQLException

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true)

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### doTwoPhaseAction

          public void doTwoPhaseAction(int nsites,
                                       int action,
                                       String[] dbnames,
                                       Xid[] xids)
                                throws XAException

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true)

    <!-- -->

    - #### doDoTwoPhaseAction

          protected int doDoTwoPhaseAction(int nsites,
                                           int action,
                                           String[] dbnames,
                                           Xid[] xids)
                                    throws XAException

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true)

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleXAResource.md)
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleXAHeteroResource.md)
- Next Class

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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
