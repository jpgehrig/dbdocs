The `BatchSQLException` class provides methods for handling batch processing errors. Because `BatchSQLException` class is derived from the [SQLException Class](sqlexecption-class.md), all `BatchSQLException` instances support all methods of `SQLException`, in addition to the methods summarized in Table 13-6.

**See Also:**

"[Modifying Rows Iteratively](optimizing-performance-of-cplusplus-applications.md)" section in [Optimizing Performance of C++ Applications](optimizing-performance-of-cplusplus-applications.md).

Table 13-6 Summary of BatchSQLException Methods

| Method              | Summary                                                           |
|:--------------------|:------------------------------------------------------------------|
| getException()      | Returns the exception.                                            |
| getFailedRowCount() | Returns the number of rows with failed inserts or updates.        |
| getRowNum()         | Returns the number of the row that has an insert or updated error |

### 13.5.1 getException()

Returns the exception that matches the specified `index`.

#### Syntax

    SQLException getSQLException (
       unsigned int index) const;

| Parameter | Description                                                      |
|:----------|:-----------------------------------------------------------------|
| `index`   | The index into the list of errors returned by the batch process. |

### 13.5.2 getFailedRowCount()

Returns the number of rows for which the statement insert or update failed.

#### Syntax

    unsigned int getFailedRowCount( ) const;

### 13.5.3 getRowNum()

Returns the number of the row with an error, matching the specified `index`.

#### Syntax

    unsigned int getRowNum(
       unsigned int index) const;

| Parameter | Description                                                      |
|:----------|:-----------------------------------------------------------------|
| `index`   | The index into the list of errors returned by the batch process. |
