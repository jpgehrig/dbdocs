## B  Configuring OCI and JDBC Applications for Column Authorization

This appendix contains:

- About Using OCI to Retrieve Column Authorization Indicators

- About Using JDBC to Retrieve Column Authorization Indicators

### B.1 About Using OCI to Retrieve Column Authorization Indicators

Oracle Call Interface (OCI) applications can access database tables that have data security policies enabled and then test columns for authorization indicators.

- If the column is determined to be unauthorized to the user, a null column value is returned to the user with indicator "unauthorized".

- If the column authorization cannot be determined, the evaluated column (or column expression) value will be returned to the user along with the indicator "unknown." If any of the underlying table columns involved in the top column expression evaluation is unauthorized, the authorization indicator can be "unknown" and a null value will be used as the underlying column value for expression valuation.

- If the column is determined as authorized to the user, the evaluated column value and indicator will be returned to the user without authorization indicator.

The OCI return code is to communicate column authorization information to the user. To obtain the authorization information for a column, you must provide a return-code buffer when the column buffer is bound or defined. After the column data is returned to the user buffer, you can check the return code associated with the column for authorization information. The column authorization indicator is applicable to define variables or out-bind variables defined by the application. The return code buffer does not have to be provided if the application is not retrieving the column authorization indicator.

This section describes the following topics:

- Example of Obtaining the Return Code

- About Using the Return Code and Indicator with Authorization Indicator

- About the Warning for Unknown Authorization Indicator

- Using OCI Describe for Column Security

#### B.1.1 Example of Obtaining the Return Code

The following return codes are used to find the column authorizations:

- ORA-24530: column value is unauthorized to the user

- ORA-24531: column value authorization is unknown

- ORA-24536: column authorization unknown

If the unknown value authorization indicator (ORA-24531) is returned for any column, the OCI function status will be `OCI_SUCCESS_WITHINFO` and the error ORA-24536 will be returned in the error handle as warning. To suppress the warning, the application can set attribute, `OCI_ATTR_NO_COLUMN_AUTH_WARNING` to `TRUE` in the statement handle before fetching:

     no_warning = TRUE;
     OCIAttrSet(stmthp, OCI_HTYPE_STMT, (void *)&no_warning, 0,
                OCI_ATTR_NO_COLUMN_AUTH_WARNING, errhp);

The default boolean value of `OCI_ATTR_NO_COLUMN_AUTH_WARNING` is `FALSE`.

Example B-1 shows OCI code that retrieves the return codes.

Example B-1 Retrieving Return Codes from OCI for a Column Authorization

    OCIDefineByPos(stmthp, &dfnhp, errhp,  1, (void *)data_bufp,  (sb4)data_bufl,
                   data_typ, (void *)&data_ind, (ub2 *)&data_rlen,
                   (ub2 *)&data_rcode, (ub4)OCI_DEFAULT);
    status = OCIStmtFetch(stmthp, errhp, 1, OCI_FETCH_NEXT, OCI_DEFAULT);
    if (data_rcode == 24530)
        printf("column value not authorized, indicator=%d\n", data_ind);
    else if (data_rcode == 24531)
             printf("column value authorization unknown, indicator=%d\n", data_ind);
    else  {
           printf("column value authorized, indicator=%d\n", data_ind);
           /* process column data */
           ...
    };

#### B.1.2 About Using the Return Code and Indicator with Authorization Indicator

To access tables with column security, you should access the return code at least when the column is bound or defined. If the return code is not accessed, the application needs to know if the column value is authorized with other means so that it can correctly interpret the indicator and the value.

You should also provide the indicator for the bind or define if column security is enabled. If the indicator is not provided and the column value is not authorized or unknown, Oracle Database returns error ORA-1405.

If column value authorization is unknown, the authorization indicator (for ORA-24531) will take precedence over the regular return codes that may otherwise be returned to the user. For example, column null fetch (ORA-1405) and column truncation (ORA-1406) may occur at the same time when a non-null column value is returned along with unknown authorization indicator. In that case, the application gets ORA-24531 as the return code for this column, instead of getting ORA-1405 or ORA-1406. Hence the application should not rely on column return code ORA-1405 or ORA-1406 to find the exact column that is null fetched or truncated.

Table B-1 and Table B-2 summarizes the behavior of the authorization indicator, return code, indicator, and return status.

#### B.1.3 About the Warning for Unknown Authorization Indicator

If the unknown authorization indicator (ORA-24531) is returned for any column, an OCI warning is returned to the application, that is, the OCI function status will be `OCI_SUCCESS_WITH_INFO`, instead of `OCI_SUCCESS`. At the same time, ORA-24536 will be set in the error handle returned to the application.You must check this warning, examine the SQL being executed, and take appropriate action. The error ORA-24536 takes precedence over the error that is returned when the column is authorized or column security is not enabled.

If a column value is unauthorized or authorized, the OCI function status code will not be changed.

By default the column authorization warning is turned on for unknown authorizations. The application should be designed to handle the error. If the application is prepared for column security and wants to ignore any unknown authorization indicator, the OCI warning can be turned off by setting the OCI attribute, `OCI_ATTR_NO_COLUMN_AUTH_WARNING` to `TRUE` in the OCI statement handle before the column value is fetched.

Table B-1 describes the default authorization behavior for OCI return indicators.

Table B-1 Authorization Indicator Behavior (By Default)

| Column Authorization | Column Value               | IND ProvidedRC Provided                                                           | IND Not ProvidedRC Provided                                                  | IND ProvidedRC Not Provided                                             | IND Not ProvidedRC Not Provided                                    |
|:---------------------|:---------------------------|:----------------------------------------------------------------------------------|:-----------------------------------------------------------------------------|:------------------------------------------------------------------------|:-------------------------------------------------------------------|
| Unauthorized         | Any                        | OCI_SUCCESS<br>Error = 0<br>IND = -1<br>RC = 24530                                | OCI_SUCCESS<br>Error = 1405<br>IND = N/A<br>RC = 24530                       | OCI_SUCCESS<br>Error = 0<br>IND = -1<br>RC = N/A                        | OCI_SUCCESS<br>Error = 1405<br>IND =-N/A<br>RC = N/A               |
| Unknown              | Null                       | SUCCESS_WITH_INFO<br>Error = 24536 (0)<br>IND = -1<br>RC = 24531 (0)              | SUCCESS_WITH_INFO<br>Error = 24536 (1405)<br>IND = N/A<br>RC = 24531 (1405)  | SUCCESS_WITH_INFO<br>Error = 24536 (0)<br>IND = -1<br>RC = N/A          | SUCCESS_WITH_INFO<br>Error = 24536 (1405)<br>IND = N/A<br>RC = N/A |
| Unknown              | Not Null and Not Truncated | SUCCESS_WITH_INFO<br>Error = 24536 (0)<br>IND = 0<br>RC = 24531 (0)               | SUCCESS_WITH_INFO<br>Error = 24536 (0)<br>IND = N/A<br>RC = 24531 (0)        | SUCCESS_WITH_INFO<br>Error = 24536 (0)<br>IND = 0<br>RC = N/A           | SUCCESS_WITH_INFO<br>Error = 24536 (0)<br>IND = N/A<br>RC = N/A    |
| Unknown              | Not Null and Truncated     | SUCCESS_WITH_INFO<br>Error = 24536 (24345)<br>IND = data_len<br>RC = 24531 (1406) | SUCCESS_WITH_INFO<br>Error = 24536 (24345)<br>IND = N/A<br>RC = 24531 (1406) | SUCCESS_WITH_INFO<br>Error = 24536 (1406)<br>IND = data_len<br>RC = N/A | SUCCESS_WITH_INFO<br>Error = 24536 (1406)<br>IND = N/A<br>RC = N/A |

**See Also:**

[Oracle Call Interface Programmer's Guide ](../lnoci/oci-programming-basics.md)Table 2-4 shows the default fetch behavior without column security

Table B-2 describes the default behavior when the `OCI_ATTR_NO_AUTH_WARNING` parameter is set to `TRUE`.

Table B-2 Authorization Indicator Behavior (By Default) - OCI_ATTR_NO_AUTH_WARNING=TRUE

| Column Authorization | Column Value               | IND ProvidedRC Provided                                                   | IND Not ProvidedRC Provided                                          | IND ProvidedRC Not Provided                 | IND Not ProvidedRC Not Provided       |
|:---------------------|:---------------------------|:--------------------------------------------------------------------------|:---------------------------------------------------------------------|:--------------------------------------------|:--------------------------------------|
| Unknown              | Null                       | Error = 0<br>IND = -1<br>RC = 24531 (0)                                   | Error = 1405<br>IND = N/A<br>RC = 24531 (1405)                       | Error = 0<br>IND = -1<br>RC = N/A)          | Error = 1405<br>IND = N/A<br>RC = N/A |
| Unknown              | Not Null and Not Truncated | Error = 0<br>IND = 0<br>RC = 24531 (0)                                    | Error = 0<br>IND = N/A<br>RC = 24531 (0)                             | Error = 0<br>IND = 0<br>RC = N/A            | Error = 0<br>IND = N/A<br>RC = N/A    |
| Unknown              | Not Null and Truncated     | SUCCESS_WITH_INFO<br>Error = 24345<br>IND = data_len<br>RC = 24531 (1406) | SUCCESS_WITH_INFO<br>Error = 24345<br>IND = N/A<br>RC = 24531 (1406) | Error = 1406<br>IND = data_len<br>RC = N/A) | Error = 1406<br>IND = N/A<br>RC = N/A |

#### B.1.4 Using OCI Describe for Column Security

The `OCIDescribeAny()` function enables an explicit describe of schema objects. Applications sometimes need to know if a column is protected by a column constraint before fetching data. You can use this information to guide the application to process the data and indicators. This is especially useful to applications that handle dynamic SQL. The attribute `OCI_ATTR_XDS_POLICY_STATUS` for the OCI parameter handle is of data type `ub4` and has the following possible values:

- `OCI_XDS_POLICY_NONE`: No XDS policy for the column or the policy is not enabled

- `OCI_XDS_POLICY_ENABLED`: policy is enabled for the column

- `OCI_XDS_POLICY_UNKNOWN`: policy unknown

If the column status is `OCI_XDS_POLICY_NONE`, then the column values will always be "authorized." If the column status is `OCI_XDS_POLICY_ENABLED`, then the column values will be either "authorized" or "unauthorized." If the column status is `OCI_XDS_POLICY_UNKNOWN`, the column value authorization will always be "unknown."

Example B-2 shows how to use the `OCIDescribeAny()` function to perform an explicit describe on a set of schema objects.

**See Also:**

[Oracle Call Interface Programmer's Guide](../lnoci/describing-schema-metadata.md)

Example B-2 Using the OCIDescribeAny Function to Enable an Explicit Describe

    void desc_explicit()
    {
      const char *table = "col_sec_tab";
      ub4 pos;
      ub2 numcol;
      OCIParam *paramh;
      OCIParam *collst;
      OCIParam *col;
      ub4 colnamelen, colseclen;
      ub1 colname[20];
      ub1 *colnm;
      ub4 colsec;
      ub4 tablen = strlen((char *)table);

      checkerr(errhp, OCIDescribeAny(svchp, errhp, (dvoid *)table, tablen,
                                     OCI_OTYPE_NAME, 0, OCI_PTYPE_TABLE, deschp));

      checkerr(errhp, OCIAttrGet(deschp, OCI_HTYPE_DESCRIBE, &paramh, 0,
                                 OCI_ATTR_PARAM, errhp));

      checkerr(errhp, OCIAttrGet(paramh, OCI_DTYPE_PARAM, &numcol, 0,
                                 OCI_ATTR_NUM_COLS, errhp));


      checkerr(errhp, OCIAttrGet(paramh, OCI_DTYPE_PARAM, &collst, 0,
                                 OCI_ATTR_LIST_COLUMNS, errhp));

      printf("Number of columns = %d\n\n", numcol);

      printf(" Column No   Column Name   Column Security\n");
      printf(" ---------   -----------   ---------------\n\n");


      for (pos = 1; (ub4) pos <= numcol; pos++)
      {
        checkerr(errhp, OCIParamGet (collst, OCI_DTYPE_PARAM, errhp,
                                     (dvoid **)&col, pos));

        checkerr(errhp, OCIAttrGet ((dvoid *)col, (ub4) OCI_DTYPE_PARAM,
                                    (dvoid **)&colnm, (ub4 *) &colnamelen,
                                    (ub4) OCI_ATTR_NAME, errhp));

        memset (colname, ' ', 20);
        strncpy((char *)colname, (char *)colnm, colnamelen);
        colname[10] = '\0';

        checkerr(errhp, OCIAttrGet ((dvoid *)col, (ub4) OCI_DTYPE_PARAM,
                                    (dvoid **)&colsec, (ub4 *) &colseclen,
                                    (ub4) OCI_ATTR_XDS_POLICY_STATUS, errhp));

        printf("    %d         %s     %s\n", pos, colname,
                               ((colsec == OCI_XDS_POLICY_ENABLED) ? "ENABLED" :
                               ((colsec == OCI_XDS_POLICY_NONE)   ?  "NONE"    :
                               ((colsec == OCI_XDS_POLICY_UNKNOWN) ? "UNKNOWN" :
                                                                     "ERROR"))));
      }

      return;
    }

### B.2 About Using JDBC to Retrieve Column Authorization Indicators

JDBC applications can access database tables that have data security policies enabled, and test columns for authorization indicators. You can use the JDBC APIs described in this section to check the security attributes and user authorization for a table column.

This section contains:

- About Checking Security Attributes for a Table Column

- About Checking User Authorization for a Table Column

- Example of Checking Security Attributes and User Authorization

#### B.2.1 About Checking Security Attributes for a Table Column

The `getSecurityAttribute` method of the `oracle.jdbc.OracleResultSetMetaData` interface enables you to check the data security policy attribute for a column. The security attribute has the following definition:

    public static enum SecurityAttribute
      {
        NONE,
        ENABLED,
        UNKNOWN;
      }

`SecurityAttribute` can have the following values:

- `NONE` implies that no column data security policy is enabled for the column. This means that the column either does not have a policy applied to it, or the policy is not enabled.

- `ENABLED` implies that column data security policy is enabled for the column.

- `UNKNOWN` implies that the column data security policy for the column is unknown. This could happen, for example, if the column is a union of two columns but only one of the columns has data security attributes.

The `getSecurityAttribute` method has the following signature:

    public SecurityAttribute getSecurityAttribute(int indexOfColumnInResultSet) throws SQLException;

The `getSecurityAttribute` method returns the `SecurityAttribute` value for the column.

**See Also:**

Example B-3 for an example of using the `getSecurityAttribute` method

#### B.2.2 About Checking User Authorization for a Table Column

The `getAuthorizationIndicator` method of the `oracle.jdbc.OracleResultSet` interface enables you to check the `AuthorizationIndicator` attribute for a column. The `AuthorizationIndicator` attribute has the following definition:

    public static enum AuthorizationIndicator
      {
        NONE,
        UNAUTHORIZED,
        UNKNOWN;
      }

`AuthorizationIndicator` can have the following values:

- `NONE` implies that access to column data is authorized. The user might have explicit authorization or the column could be lacking security attributes.

- `UNAUTHORIZED` implies that access to column data is not authorized.

  When the column value is retrieved, the authorization indicator is evaluated based on the enabled column constraint policy for the column. If the user is not authorized to access the column value, a `NULL` value is returned to the application along with the authentication indicator, `AuthorizationIndicator.UNAUTHORIZED`.

  If there is a column expression involving the unauthorized base column, the evaluated value is returned to the application along with the `AuthorizationIndicator.UNAUTHORIZED` indicator. The application should examine the authorization indicator before interpreting the returned data.

- `UNKNOWN` implies that the authorization indicator cannot be determined.

  Sometimes, the server fails to determine the authorization indicator for a `SELECT` item due to functionality limitations or performance constrains. This can happen if the query involves a column expression, for example, and the server is unable to compute whether the top operator is supposed to be authorized. In such a scenario, the server returns the authorization indicator, `AuthorizationIndicator.UNKNOWN` to the application. The returned value can be `NULL` or not `NULL` depending on how the column expression operates on the underlying column value.

  If the application sees an `UNKNOWN` authorization indictor, it should determine whether or not the returned value should be accessed. If the query and its column expressions are designed to handle unauthorized `NULL` values from the underlying columns, then the application can use the returned value. Otherwise the application may have to take appropriate actions for the returned value.

The `getAuthorizationIndicator` method has the following forms:

    /**
     * Accepts the column index number as an argument and retrieves the corresponding column security AuthorizationIndicator value
     */
    public AuthorizationIndicator getAuthorizationIndicator(int columnIndex) throws SQLException;

    /**
     * Accepts the column name as a string and retrieves the column security AuthorizationIndicator value
     */
    public AuthorizationIndicator getAuthorizationIndicator(String columnName)throws SQLException;

**Note:**

- The preceding methods throw a `SQLException` if the index specified in the argument is invalid.

- If a column is masked, the JDBC user sees it as a NULL value. An exception is not thrown for this.

**See Also:**

Example B-3 for an example of using the `getAuthorizationIndicator` method

#### B.2.3 Example of Checking Security Attributes and User Authorization

Example B-3 illustrates the use of the `getSecurityAttribute` and `getAuthorization` methods to check security attributes and user authorization. The program uses the sample `EMP` table to illustrate the procedure.

The `EMP` table is configured as follows:

| Column No. | Column Title | Security Attribute         |
|:-----------|:-------------|:---------------------------|
| 1          | `EMPNO`      | No security attribute      |
| 2          | `ENAME`      | Active security            |
| 3          | `JOB`        | No security attribute      |
| 4          | `MGR`        | Active security            |
| 5          | `HIREDATE`   | Unknown security attribute |
| 6          | `SAL`        | Active security            |
| 7          | `COMM`       | No security attribute      |
| 6          | `DEPTNO`     | Active security            |

The program performs the following actions:

1.  Selects rows from the `EMP` table
2.  Uses the `getSecurityAttribute` method to extract the security setting for each column in the result set. It prints these as column headings
3.  Uses the `getAuthorizationIndicator` method to check the user authorization for returned column values. The program prints these values and formats them as follows:
    An unauthorized value that is returned as `NULL` is represented by four asterisk characters (`****`).

Example B-3 Check Security Attributes and User Authorization

    PreparedStatement pstmt = conn.prepareStatement("SELECT * FROM EMP");
      ResultSet rs = pstmt.executeQuery();
      OracleResultSetMetaData metaData =
       (OracleResultSetMetaData)rs.getMetaData();
      int nbOfColumns = metaData.getColumnCount();
      OracleResultSetMetaData.SecurityAttribute[] columnSecurity
        = new OracleResultSetMetaData.SecurityAttribute[nbOfColumns];
      // display which columns are protected:
      for(int i=0;i<nbOfColumns;i++)
      {
        columnSecurity[i] = metaData.getSecurityAttribute(i+1);
        System.out.print(columnSecurity[i]);
        System.out.print("\t");
      }
      System.out.println();
      System.out.println("---------------------------------------------");
      while(rs.next())
      {
        for(int colIndex=0;colIndex<nbOfColumns;colIndex++)
        {
          OracleResultSet.AuthorizationIndicator visibility
            = ((OracleResultSet)rs).getAuthorizationIndicator(colIndex+1);
          if(visibility == OracleResultSet.AuthorizationIndicator.UNAUTHORIZED)
            System.out.print("****");
          else
            System.out.print(rs.getString(colIndex+1));
          System.out.print("\t");
        }
        System.out.println("");
      }
      rs.close();
      pstmt.close();

The program generates the following output:

    NONE   ENABLED   NONE       ENABLED   UNKNOWN      ENABLED   NONE   ENABLED
    ----------------------------------------------------------------------------------
    7369   SMITH     CLERK      7902      1980-12-17   ****      null   20
    7499   ALLEN     SALESMAN   7698      1981-02-20   ****      300    30
    7521   WARD      SALESMAN   7698      1981-02-22   ****      500    30
    7566   JONES     MANAGER    7839      1981-04-02   ****      null   20
    7654   MARTIN    SALESMAN   7698      1981-09-28   ****      1400   30
    7698   BLAKE     MANAGER    7839      1981-05-01   ****      null   30
    7782   CLARK     MANAGER    7839      1981-06-09   ****      null   10
    7788   SCOTT     ANALYST    7566      1987-04-19   ****      null   20
    7839   KING      PRESIDENT  null      1981-11-17   ****      null   10
    7844   TURNER    SALESMAN   7698      1981-09-08   ****      0      30
    7876   ADAMS     CLERK      7788      1987-05-23   ****      null   20
    7900   JAMES     CLERK      7698      1981-12-03   ****      null   30
    7902   FORD      ANALYST    7566      1981-12-03   ****      null   20
    7934   MILLER    CLERK      7782      1982-01-23   ****      null   10
