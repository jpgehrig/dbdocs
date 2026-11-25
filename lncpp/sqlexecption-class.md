The `SQLException` class provides information on generated errors, their codes and associated messages.

Table 13-40 Summary of SQLException

| Method                 | Description                                                               |
|:-----------------------|:--------------------------------------------------------------------------|
| SQLException()         | `SQLException` constructor.                                               |
| getErrorCode()         | Returns the database error code.                                          |
| getMessage()           | Returns the error message `string` for this exception.                    |
| getNLSMessage()        | Returns the error message `string` for this exception (Unicode support).  |
| getNLSUStringMessage() | Returns the error message `UString` for this exception (Unicode support). |
| getUStringMessage()    | Returns the error message `UString` for this exception.                   |
| getXAErrorCode()       | Returns the error message string for this exception.                      |
| isRecoverable()        | Determines whether an application can failover and recover from an error. |
| setErrorCtx()          | Sets the error context.                                                   |
| what()                 | Returns the error message associated with the `SQLException`.             |

### 13.28.1 SQLException()

This is the `SQLException` constructor.

| Syntax                                          | Description                                                                     |
|:------------------------------------------------|:--------------------------------------------------------------------------------|
| `SQLException();`                               | Constructs a `NULL SQLException` object.                                        |
| `SQLException(`<br>`   const SQLException &e);` | Constructs an `SQLException` object as a copy of another `SQLException` object. |

| Parameter | Description                      |
|:----------|:---------------------------------|
| `e`       | The `SQLException` to be copied. |

### 13.28.2 getErrorCode()

Gets the database error code.

#### Syntax

    int getErrorCode() const;

### 13.28.3 getMessage()

Returns the error message string of this `SQLException` if it was created with an error message string. Returns `NULL` if the `SQLException` was created with no error message.

#### Syntax

    string getMessage() const;

### 13.28.4 getNLSMessage()

Returns the error message `string` of this `SQLException` if it was created with an error message `string`. Passes the globalization enabled environment. Returns a `NULL string` if the `SQLException` was created with no error message. The error message is in the character set associated with the environment.

#### Syntax

    string getNLSMessage(
       Environment *env) const;

| Parameter | Description                            |
|:----------|:---------------------------------------|
| `env`     | The globalization enabled environment. |

### 13.28.5 getNLSUStringMessage()

Returns the error message `UString` of this `SQLException` if it was created with an error message `UString`. Passes the globalization enabled environment. Returns a `NULL UString` if the `SQLException` was created with no error message. The error message is in the character set associated with the environment.

#### Syntax

    UString getNLSUStringMessage(
       Environment *env) const;

| Parameter | Description                            |
|:----------|:---------------------------------------|
| `env`     | The globalization enabled environment. |

### 13.28.6 getUStringMessage()

Returns the error message `UString` of this `SQLException` if it was created with an error message `UString`. Returns a `NULL UString` if the `SQLException` was created with no error message. The error message is in the character set associated with the environment.

#### Syntax

    UString getUStringMessage() const;

### 13.28.7 getXAErrorCode()

Determine if the thrown exception is due to an XA or an SQL error.

Used by C++ XA applications with dynamic registration. Returns an XA error code if the exception is due to XA, or` XA_OK` otherwise.

#### Syntax

    int getXAErrorCode(
       const string &dbname) const;

| Parameter | Description                                                                                                                    |
|:----------|:-------------------------------------------------------------------------------------------------------------------------------|
| `dbname`  | The database name; same as the optional `dbname` provided in the Open String and used when connecting to the Resource Manager. |

### 13.28.8 isRecoverable()

Determines whether an application can failover and recover from an error. Returns `TRUE` if recoverable.

For example, an application may recover from `ORA-03113`, but not from `ORA-942`.

#### Syntax

    bool isRecoverable();

### 13.28.9 setErrorCtx()

Sets the pointer to the error context.

#### Syntax

    void setErrorCtx(
       void *ctx);

| Parameter | Description                       |
|:----------|:----------------------------------|
| `ctx`     | The pointer to the error context. |

### 13.28.10 what()

Standard C++ compliant function; returns the error message associated with the `SQLException`.

#### Syntax

    const char *what() const throw();
