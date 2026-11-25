## 147  DBMS_RESULT_CACHE

The `DBMS_RESULT_CACHE` package provides an interface to allow the DBA to administer that part of the shared pool that is used by the SQL result cache and the PL/SQL function result cache.

Both these caches use the same infrastructure. Therefore, for example, `DBMS_RESULT_CACHE`.`BYPASS` determines whether both caches are bypassed or both caches are used, and `DBMS_RESULT_CACHE`.`FLUSH` flushes both all the cached results for SQL queries and all the cached results for PL/SQL functions.

This chapter contains the following topics:

- Security Model

- Constants

- Summary of DBMS_RESULT_CACHE Subprograms

**See Also:**

- Oracle Database PL/SQL Language Reference for more information about ["Using the Cross-Session PL/SQL Function Result Cache"](../lnpls/pl-sql-function-result-cache.md)

- Oracle Database Performance Tuning Guide for more information about ["Result Cache Concepts"](../tgdba/tuning-result-cache.md)

### 147.1 DBMS_RESULT_CACHE Security Model

Only database administrators should be granted the `EXECUTE` privilege for this package.

### 147.2 DBMS_RESULT_CACHE Constants

The `DBMS_RESULT_CACHE` package defines several constants for specifying parameter values.

The following table describes these constants.

Table 147-1 DBMS_RESULT_CACHE Constants

| Constant      | Definition                             | Description                                                  |
|:--------------|:---------------------------------------|:-------------------------------------------------------------|
| `STATUS_BYPS` | `CONSTANT VARCHAR2(10) := 'BYPASS';`   | Cache has been made temporarilyunavailable.                  |
| `STATUS_CORR` | `CONSTANT VARCHAR2(10) := 'CORRUPT';`  | The result cache is in an unusable state.                    |
| `STATUS_DISA` | `CONSTANT VARCHAR2(10) := 'DISABLED';` | Cache is not available.                                      |
| `STATUS_ENAB` | `CONSTANT VARCHAR2(10) := 'ENABLED';`  | Cache is available.                                          |
| `STATUS_SYNC` | `CONSTANT VARCHAR2(10) := 'SYNC'; `    | Cache is available, but synchronizing with Oracle RAC nodes. |

### 147.3 Summary of DBMS_RESULT_CACHE Subprograms

This table lists the `DBMS_RESULT_CACHE` subprograms and briefly describes them.

Table 147-2 DBMS_RESULT_CACHE Package Subprograms

| Subprogram                               | Description                                                                                                                                                  |
|:-----------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| BLACK_LIST Function                      | Returns a pipelined BL_TABT.                                                                                                                                 |
| BLACK_LIST_ADD Procedure                 | Adds a `cache_id` to the black-list.                                                                                                                         |
| BLACK_LIST_CLEAR Procedure               | Removes all cache_ids from the black-list.                                                                                                                   |
| BLACK_LIST_REMOVE Procedure              | Removes the cache_id from the black-list.                                                                                                                    |
| BYPASS Procedure                         | Sets the bypass mode for the Result Cache                                                                                                                    |
| FLUSH Function & Procedure               | Attempts to remove all the objects from the Result Cache, and depending on the arguments retains or releases the memory and retains or clears the statistics |
| INVALIDATE Functions & Procedures        | Invalidates all the result-set objects that dependent upon the specified dependency object                                                                   |
| INVALIDATE_OBJECT Functions & Procedures | Invalidates the specified result-set object(s)                                                                                                               |
| MEMORY_REPORT Procedure                  | Produces the memory usage report for the Result Cache                                                                                                        |
| STATUS Function                          | Checks the status of the Result Cache                                                                                                                        |

#### 147.3.1 BLACK_LIST Function

This table function returns all the blocklisted cache ids of a local instance.

##### Syntax

    DBMS_RESULT_CACHE.BLACK_LIST
       RETURN BL_TABT;

#### 147.3.2 BLACK_LIST_ADD Procedure

This procedure adds a cache_id to the blocklist.

##### Syntax

    DBMS_RESULT_CACHE.BLACK_LIST_ADD (
       cache_id   IN  VARCHAR2,
       global     IN  BOOLEAN DEFAULT FALSE);

##### Parameters

Table 147-3 BLACK_LIST_ADD Procedure Parameters

| Parameter  | Description                                                                                                       |
|:-----------|:------------------------------------------------------------------------------------------------------------------|
| `cache_id` | The `cache_id` is added to the blocklist.                                                                         |
| `global`   | `TRUE` — applies to all caches in a RAC cluster.<br>`FALSE` (default) — applies only to the local instance cache. |

#### 147.3.3 BLACK_LIST_CLEAR Procedure

This procedure removes all cache_ids from the blocklist.

##### Syntax

    DBMS_RESULT_CACHE.BLACK_LIST_CLEAR (
       global   IN  BOOLEAN DEFAULT FALSE);

##### Parameters

Table 147-4 BLACK_LIST_CLEAR Procedure Parameters

| Parameter | Description                                                                                                       |
|:----------|:------------------------------------------------------------------------------------------------------------------|
| `global`  | `TRUE` — applies to all caches in a RAC cluster.<br>`FALSE` (default) — applies only to the local instance cache. |

#### 147.3.4 BLACK_LIST_REMOVE Procedure

This procedures removes the cache_id from the blocklist.

##### Syntax

    DBMS_RESULT_CACHE.BLACK_LIST_REMOVE (
       cache_id   IN  VARCHAR2,
       global     IN  BOOLEAN DEFAULT FALSE);

##### Parameters

Table 147-5 BLACK_LIST_REMOVE Procedure Parameters

| Parameter  | Description                                                                                                       |
|:-----------|:------------------------------------------------------------------------------------------------------------------|
| `cache_id` | The `cache_id` is removed from the blocklist.                                                                     |
| `global`   | `TRUE` — applies to all caches in a RAC cluster.<br>`FALSE` (default) — applies only to the local instance cache. |

#### 147.3.5 BYPASS Procedure

This procedure sets the bypass mode for the Result Cache.

It sets one of the following bypass modes:

- When bypass mode is turned on, it implies that cached results are no longer used and that no new results are saved in the cache.

- When bypass mode is turned off, the cache resumes normal operation.

##### Syntax

    DBMS_RESULT_CACHE.BYPASS (
       bypass_mode    IN   BOOLEAN,
       session        IN   BOOLEAN);

##### Parameters

Table 147-6 BYPASS Procedure Parameters

| Parameter     | Description                                                                                  |
|:--------------|:---------------------------------------------------------------------------------------------|
| `bypass_mode` | • `TRUE` =\> Result Cache usage is bypassed<br>• `FALSE` =\> Result Cache usage is turned on |
| `session`     | • `TRUE` =\> Applies to current session<br>• `FALSE` (default) =\> Applies to all sessions   |

##### Usage Notes

This operation is database instance specific.

##### Examples

This operation can be used when there is a need to hot patch PL/SQL code in a running system. If a code-patch is applied to a PL/SQL module on which a result cached function directly or transitively depends, then the cached results associated with the result cache function are not automatically flushed (if the instance is not restarted/bounced). This must be manually achieved.

To ensure correctness during the patching process follow these steps:

1.  Place the result cache in bypass mode, and flush existing result.

        BEGIN
           DBMS_RESULT_CACHE.BYPASS(TRUE);
           DBMS_RESULT_CACHE.FLUSH;
        END;
        /

    This step must be performed on each instance if in a Oracle Real Application Clusters environment.

2.  Apply the PL/SQL code patches.

3.  Resume use of the result cache, by turning off the cache bypass mode.

        BEGIN
           DBMS_RESULT_CACHE.BYPASS(FALSE);
        END;
        /

    This step must be performed on each instance if in a Oracle Real Application Clusters environment.

#### 147.3.6 FLUSH Function & Procedure

This function and procedure attempts to remove all the objects from the Result Cache, and depending on the arguments retains or releases the memory and retains or clears the statistics.

##### Syntax

    DBMS_RESULT_CACHE.FLUSH (
       retainMem  IN  BOOLEAN DEFAULT FALSE,
       retainSta  IN  BOOLEAN DEFAULT FALSE)
      RETURN BOOLEAN;

    DBMS_RESULT_CACHE.FLUSH (
       retainMem  IN  BOOLEAN DEFAULT FALSE,
       retainSta  IN  BOOLEAN DEFAULT FALSE);

##### Parameters

Table 147-7 FLUSH Function & Procedure Parameters

| Parameter   | Description                                                                                                         |
|:------------|:--------------------------------------------------------------------------------------------------------------------|
| `retainMem` | • `TRUE` =\> retains the free memory in the cache<br>• `FALSE` (default) =\> releases the free memory to the system |
| `retainSta` | • `TRUE` =\> retains the existing cache statistics<br>• `FALSE` (default) =\> clears the existing cache statistics  |

##### Return Values

`TRUE` if successful in removing all the objects.

#### 147.3.7 INVALIDATE Functions & Procedures

This function and procedure invalidates all the result-set objects that dependent upon the specified dependency object.

##### Syntax

    DBMS_RESULT_CACHE.INVALIDATE (
       owner        IN  VARCHAR2,
       name         IN  VARCHAR2)
     RETURN NUMBER;

    DBMS_RESULT_CACHE.INVALIDATE (
       owner       IN  VARCHAR2,
       name        IN  VARCHAR2);

    DBMS_RESULT_CACHE.INVALIDATE (
      object_id    IN BINARY_INTEGER)
     RETURN NUMBER;

    DBMS_RESULT_CACHE.INVALIDATE (
       object_id    IN BINARY_INTEGER);

##### Parameters

Table 147-8 INVALIDATE Function & Procedure Parameters

| Parameter   | Description              |
|:------------|:-------------------------|
| `owner`     | Schema name              |
| `name`      | Object name              |
| `object_id` | Dictionary object number |

##### Return Values

The number of objects invalidated.

#### 147.3.8 INVALIDATE_OBJECT Functions & Procedures

This function and procedure invalidates the specified result-set object(s).

##### Syntax

    DBMS_RESULT_CACHE.INVALIDATE_OBJECT (
       id          IN  BINARY_INTEGER)
     RETURN NUMBER;

    DBMS_RESULT_CACHE.INVALIDATE_OBJECT (
       id          IN  BINARY_INTEGER);

    DBMS_RESULT_CACHE.INVALIDATE_OBJECT (
      cache_id     IN  VARCHAR2)
     RETURN NUMBER;

    DBMS_RESULT_CACHE.INVALIDATE_OBJECT (
       cache_id   IN  VARCHAR2);

##### Parameters

Table 147-9 INVALIDATE_OBJECT Function & Procedure Parameters

| Parameter  | Description                                                 |
|:-----------|:------------------------------------------------------------|
| `id`       | Address of the cache object in the Result Cache             |
| `cache_id` | Result cache identifier of a SQL cursor or PL/SQL function. |

##### Return Values

The number of objects invalidated.

#### 147.3.9 MEMORY_REPORT Procedure

This procedure produces the memory usage report for the Result Cache.

##### Syntax

    DBMS_RESULT_CACHE.MEMORY_REPORT (
       detailed   IN   BOOLEAN DEFAULT FALSE);

##### Parameters

Table 147-10 MEMORY_REPORT Procedure Parameters

| Parameter  | Description                                                                                          |
|:-----------|:-----------------------------------------------------------------------------------------------------|
| `detailed` | • `TRUE` =\> produces a more detailed report<br>• `FALSE` (default) =\> produces the standard report |

##### Usage Notes

Invoking this procedure from SQL\*Plus requires that the serveroutput be turned on.

##### Examples

    SET SERVEROUTPUT ON

    EXECUTE DBMS_RESULT_CACHE.MEMORY_REPORT;

#### 147.3.10 STATUS Function

This function checks the status of the Result Cache.

##### Syntax

    DBMS_RESULT_CACHE.STATUS
       RETURN VARCHAR2;

**Note:**

For more information on the constants, see DBMS_RESULT_CACHE Constants.
