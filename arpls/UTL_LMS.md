## 272  UTL_LMS

`UTL_LMS` retrieves and formats error messages in different languages.

This chapter contains the following topics:

- Security Model

- Summary of UTL_LMS Subprograms

**See Also:**

[Oracle Database Globalization Support Guide](../nlspg/oracle-globalization-development-kit.md)

### 272.1 UTL_LMS Security Model

This package must be created as the user `SYS`.

### 272.2 Summary of UTL_LMS Subprograms

This table lists the `UTL_LMS` subprograms and briefly describes them.

Table 272-1 UTL_LMS Package Subprograms

| Function                | Description                                                                                          |
|:------------------------|:-----------------------------------------------------------------------------------------------------|
| FORMAT_MESSAGE Function | Formats a retrieved error message                                                                    |
| GET_MESSAGE Function    | Retrieves an error message based on error number, product, facility, language, and message specified |

#### 272.2.1 FORMAT_MESSAGE Function

This function formats a message retrieved by the `GET_MESSAGE` function and returns the formatted message. If the function fails, then it returns a `NULL` result.

The following table shows special characters that can be used in the format string.

| Special Character | Description                          |
|:------------------|:-------------------------------------|
| `'%s'`            | Substitute the next string argument  |
| `'%d'`            | Substitute the next integer argument |
| `'%%'`            | Represents the special character `%` |

##### Syntax

    UTL_LMS.FORMAT_MESSAGE (
       format IN VARCHAR2 CHARACTER SET ANY_CS,
       args   IN VARCHAR2 CHARACTER SET ANY_CS DEFAULT NULL)
     RETURN VARCHAR2 CHARACTER SET format%CHARSET;

##### Parameters

Table 272-2 FORMAT_MESSAGE Procedure Parameters

| Parameter | Description                     |
|:----------|:--------------------------------|
| `format`  | Specifies the string to format  |
| `args`    | Specifies the list of arguments |

##### Examples

    DECLARE
       s varchar2(200);
       i  pls_integer;
    BEGIN
       i:= utl_lms.get_message(26052, 'rdbms', 'ora', 'french', s);
       dbms_output.put_line('before format, message is: '||s);
       dbms_output.put_line('formatted message is: '||utl_lms.format_message(s, 9, 'my_column_name');
    END;
    /

The following is an unformatted message:

    Type %d non pris en charge pour l'expression SQL sur la colonne %s.

The following is the formatted message:

    Type 9 non pris en charge pour l'expression SQL sur la colonne my_column_name.

#### 272.2.2 GET_MESSAGE Function

This function retrieves an Oracle error message. The user can define user-specific error messages with the `lmsgen` utility.

It returns `0` when it is successful. It returns `-1` when it fails.

**See Also:**

[Oracle Database Globalization Support Guide ](../nlspg/OCI-programming-in-global-environment.md)for more information about the `lmsgen` utility

##### Syntax

    UTL_LMS.GET_MESSAGE (
       errnum    IN PLS_INTEGER,
       product   IN VARCHAR2,
       facility  IN VARCHAR2,
       language  IN VARCHAR2,
       message   OUT NOCOPY VARCHAR2CHARCTER SET ANY_CS)
    RETURN PLS_INTEGER;

##### Parameters

Table 272-3 GET_MESSAGE Function Parameters

| Parameter  | Description                                                                                                                                                                           |
|:-----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `errnum`   | Specifies the error number.<br>Example: `'972'` (for `ORA-00972)`                                                                                                                     |
| `product`  | Specifies the product to which the error message applies<br>Example: '`rdbms`'                                                                                                        |
| `facility` | Specifies the error message prefix<br>Example: `'ora'`                                                                                                                                |
| `language` | Specifies the language of the message. The parameter is case-insensitive. The default is `NULL`, which causes `GET_MESSAGE` to use the value of the `NLS_LANGUAGE` session parameter. |
| `message`  | Specifies the output buffer for the retrieved message                                                                                                                                 |

##### Usage Notes

If the `language` parameter is set to `NULL`, then the value of the `NLS_LANGUAGE` session parameter is used as the default.

##### Examples

    DECLARE
      s varchar2(200);
      i pls_integer;
    BEGIN
       i:=utl_lms.get_message(601, 'rdbms', 'oci', 'french', s);
       dbms_output.put_line('OCI--00601 is: '||s);
    END
    /

The following output results:

    OCI--00601 is: Echec du processus de nettoyage.
