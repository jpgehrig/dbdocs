Various relational databases enable stored procedures to return result sets (one or more sets of rows).

Traditionally, database stored procedures worked exactly like procedures in any high-level programming language. They had a fixed number of arguments which could be of types `IN`, `OUT`, or `IN OUT`. If a procedure had `n` arguments, it could return at most `n` values as results. However, suppose that you wanted a stored procedure to execute a query such as `SELECT * FROM emp` and return the results. The `emp` table might have a fixed number of columns, but there is no way of telling, at procedure creation time, the number of rows it has. Because of this, no traditional stored procedure could be created that returned the results of this type of query. As a result, several relational database vendors added the ability to return results sets from stored procedures, but each relational database returns result sets from stored procedures differently.

Oracle has a data type called a `REF CURSOR`. Like every other Oracle data type, a stored procedure can take this data type as an `IN` or `OUT` argument. With Oracle Database, a stored procedure must have an output argument of type `REF CURSOR`. It then opens a cursor for a SQL statement and places a handle to that cursor in that output parameter. The caller can then retrieve from the `REF CURSOR` the same way as from any other cursor.

Oracle Database can do a lot more than return result sets. The `REF CURSOR` data type can be passed as an input argument to PL/SQL routines to be passed back and forth between client programs and PL/SQL routines or as an input argument between several PL/SQL routines.

- Result Set Support for Non-Oracle Systems
  Several non-Oracle systems allow stored procedures to return result sets, but they do so in different ways.
- Heterogeneous Services Support for Result Sets
  Result set support exists among non-Oracle databases in different forms. All of these must be mapped to the Oracle `REF CURSOR` model.

**Parent topic:** [Features of Oracle Database Gateways](oracle-database-gateways-features.md)

### Result Set Support for Non-Oracle Systems

Several non-Oracle systems allow stored procedures to return result sets, but they do so in different ways.

Result set support for non-Oracle databases is typically based on one of the following two models.

- Model 1: Result Set Support

  When creating a stored procedure, you can explicitly specify the maximum number of result sets that can be returned by that stored procedure. While executing, the stored procedure can open anywhere from zero up to its specified maximum number of result sets. After the execution of the stored procedure, a client program gets handles to these result sets by using either an embedded SQL directive or by calling a client library function. After that, the client program can retrieve from the result set in the same way as from a typical cursor.

- Model 2: Result Set Support

  In this model, there is no specified limit to the number of result sets that can be returned by a stored procedure. Both Model 1 and Oracle Database have a limit. For Oracle Database, the number of result sets returned by a stored procedure can be at most the number of `REF CURSOR OUT` arguments. For Model 1, the upper limit is specified using a directive in the stored procedure language. Another way that Model 2 differs from Oracle Database and Model 1 is that they do not return a handle to the result sets. Instead, they place the entire result set on the wire when returning from a stored procedure. For Oracle Database, the handle is the `REF CURSOR OUT` argument. For Model 1, it is obtained separately after the execution of the stored procedure. For both Oracle Database and Model 1, after the handle is obtained, data from the result set is obtained by doing a fetch on the handle; there are several cursors open and the fetch can be in any order. In the case of Model 2, however, all the data is already on the wire, with the result sets coming in the order determined by the stored procedure and the output arguments of the procedures coming at the end. The entire first result set must be retrieved, then the entire second result set, until all of the results are retrieved. Finally, the stored procedure `OUT` arguments are retrieved.

**Parent topic:** Result Set Support

### Heterogeneous Services Support for Result Sets

Result set support exists among non-Oracle databases in different forms. All of these must be mapped to the Oracle `REF CURSOR` model.

Due to the differences in behavior among the non-Oracle systems, Heterogeneous Services result set support acts in one of two different ways depending on the non-Oracle system to which it is connected.

Note the following about Heterogeneous Services result set support:

- Result set support is part of the Heterogeneous Services generic code, but for the feature to work in a gateway, the driver has to implement it. Not all drivers have implemented result set support and you must verify that your gateway is supported.

- Heterogeneous Services supports `REF CURSOR OUT` arguments from stored procedures. `IN` and `IN OUT` arguments are not supported.

- The `REF CURSOR OUT` arguments are all anonymous reference cursors. `REF CURSOR`s that are returned by Heterogeneous Services do not have types.

<!-- -->

- Results Sets: Cursor Mode
  Each result set returned by a non-Oracle system stored procedure is mapped by an Oracle driver to an `OUT` argument of type `REF CURSOR`.
- Result Sets: Sequential Mode
  There is a maximum number of result sets that a particular stored procedure can return. The number of result sets returned is at most the number of `REF CURSOR OUT` arguments for the stored procedure. It can return fewer result sets, but it can never return more.

**Parent topic:** Result Set Support

#### Results Sets: Cursor Mode

Each result set returned by a non-Oracle system stored procedure is mapped by an Oracle driver to an `OUT` argument of type `REF CURSOR`.

The client program detects a stored procedure with several `OUT` arguments of type `REF CURSOR`. After executing the stored procedure, the client program can fetch from the `REF CURSOR` the same way as it would from a `REF CURSOR` returned by an Oracle stored procedure. When connecting to the gateway as described in Section 3.4.1.1, Heterogeneous Services will be in cursor mode.

**Parent topic:** Heterogeneous Services Support for Result Sets

#### Result Sets: Sequential Mode

There is a maximum number of result sets that a particular stored procedure can return. The number of result sets returned is at most the number of `REF CURSOR OUT` arguments for the stored procedure. It can return fewer result sets, but it can never return more.

For the system described in Section 3.4.1.2, there is no maximum number of result sets that can be returned. In the case of Model 1 (in Section 3.4.1.1), the maximum number of result sets that a procedure can return is known, and that the driver can return to Heterogeneous Services, is specified in the stored procedure by the number of `REF CURSOR OUT` arguments. If, when the stored procedure is executed, fewer result sets than the maximum are returned, then the other `REF CURSOR OUT` arguments are set to `NULL`.

Another problem for Model 2 database servers is that result sets must be retrieved in the order in which they were placed on the wire by the database. This prevents Heterogeneous Services from running in cursor mode when connecting to these databases. To access result sets returned by these stored procedures, Heterogeneous Services must be in sequential mode.

In sequential mode, the procedure description returned by the driver contains the following:

- All the input arguments of the remote stored procedure

- None of the output arguments

- One `OUT` argument of type `REF CURSOR` (corresponding to the first result set returned by the stored procedure)

The client fetches from this `REF CURSOR` and then calls the virtual package function `DBMS_HS_RESULT_SET.GET_NEXT_RESULT_SET` to fetch the `REF CURSOR` corresponding to the next result set. This function call repeats until all result sets are retrieved. The last result set returned will be the `OUT` arguments of the remote stored procedure.

The primary limitations of sequential mode are:

- Result sets returned by a remote stored procedure must be retrieved in the order in which they were placed on the wire.

- When a stored procedure is executed, all result sets returned by a previously executed stored procedure are closed (regardless of whether or not the data was retrieved).

  **See Also:**

  Your gateway-specific manual for more information about how result sets are supported through the gateway

**Parent topic:** Heterogeneous Services Support for Result Sets
