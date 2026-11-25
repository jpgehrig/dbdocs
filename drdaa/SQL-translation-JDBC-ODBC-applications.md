Oracle provides SQL Translation mechanisms for use with JDBC and ODBC applications.

### SQL Translation of JDBC Applications

Consider the concepts necessary to understanding how to use SQL Translator with a JDBC application.

#### SQL Translation Profile

A SQL Translation Profile is a database schema object that directs how SQL statements in non-Oracle dialects are translated into Oracle SQL dialects. It also directs how Oracle error codes and `SQLSTATES` are translated into the SQL dialect of other vendors.

When you want to migrate a client application written for a non-Oracle SQL database to Oracle, you can create a SQL Translation Profile and configure it to translate the SQL statements and errors for the application. At runtime, the application sets the profile for the connection in Oracle Database to translate its SQL statements and errors. This profile is set using the `oracle.jdbc.sqlTranslationProfile` property.

When necessary, you can register custom translations of SQL statements and errors with the SQL Translation Profile on the Server. When a SQL statement or error is translated, then first, the custom translation is looked up and then, the translator is invoked only if no match is found.

See "[Architecture of SQL Translation Framework](SQL-translation-framework-overview.md)" and "[Setting up a SQL Translation Profile](SQL-translation-framework-configuration.md)".

#### Error Message Translation

You may prefer receiving error messages in the form of messages that used to be thrown by the native database. You must then use the error message translation file, which translates error messages when there is no valid connection to the database. Once a connection to the database is established, the JDBC driver bypasses this file completely and all errors are handled by the translator on the server. Similar to query translation, you can also register custom error translations on the server.

The error message translation file is not written by a specific component. You must provide the file for translation and specify the name of the file. You can also provide the file path as the value of the corresponding connection property.

The error message translation file is in XML format; it contains a series of error translations. Each error translation contains the following information:

| Translation Error     | Type             |
|:----------------------|:-----------------|
| ORA error number      | positive integer |
| Oracle error message  | String           |
| Translated error code | positive integer |
| Translated SQL State  | positive integer |

#### Converting JDBC Standard Parameter Markers

Before submitting the SQL statements for translation., the JDBC driver internally converts the JDBC standard parameter markers (`?`) into Oracle style parameter markers of the format `:b<n>`.

Here, the naming format for the parameter markers is `:b<n>`, where `n` is an incremental number to specify the position of the (`?`) marker in the JDBC `PreparedStatement`.

Consider the `UPDATE employees SET salary = salary * ? WHERE employee_id = ?` `PreparedStatement` statement, where, the first parameter marker (`?`) will become `:b1` and the second parameter marker (`?`) will become `:b2`.

After conversion, the driver sends the following query to the server for translation:

    UPDATE employees SET salary = salary * :b1 WHERE employee_id = :b2

Note that any query that contains "?" as a parameter marker fails during the connection translation phase if you change the value of the `processEscapes` property to `FALSE`. For a successful translation, you must retain the default value of the `processEscapes` property.

Converting parameter markers helps the driver to automatically reorder any parameter changes that occurred at translation. At the time of conversion, any custom translation that must be registered on the server should be registered from the Oracle style parameter marker version; the server receives the statements. Note that, the custom translation must have the same number of parameter markers in the Oracle style as in the original query.

For more information about supported JDBC APIs, [API Reference for SQL Translation of JDBC Applications](API-ref-for-SQL-translation-of-JDBC-apps.md) .

#### Executing the Translated Oracle Dialect Query

After the JDBC standard parameter markers are converted into Oracle style parameter markers, the driver makes a round-trip to the server for translating the query into Oracle dialect. Once the translated query is received by the server, any reordering in the parameters in handled transparently by the driver, and the query is executed as a normal query.

If a query cannot be translated due to the unavailability of translation, then the server can either raise an error or return a `NULL`, based on the value of the `DBMS_SQL_TRANSLATOR.ATTR_RAISE_TRANSLATION_ERROR` profile attribute. If the server returns a `NULL`, then the original untranslated query is assumed to be the query translated by the driver and executed.

The driver keeps the translation in the local caches to save the future round-trip.

Note that the JDBC driver can support the translation errors (when the query cannot be translated due to the unavailability of translation) set by either value of the `DBMS_SQL_TRANSLATOR.ATTR_RAISE_TRANSLATION_ERROR` attribute. However, the value must be set on the server before the connection is established. Because a change in the value of this attribute in the middle of a session may result in inconsistent behavior, Oracle recommends that you do not flip the value of this attribute during a session. See [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_SQL_TRANSLATOR.md) for more information about the `TRANSLATE_SQL` procedure.

#### Error Translation

If any `SQLException` is thrown during the query execution, the driver transparently makes a trip to the server and translates the exception from Oracle codes to the original vendor-specific code. So, the resulting `SQLException` has both vendor-specific code and `SQLSTATE` along with the Oracle-specific `SQLException` as the cause.

Similar to query translation, custom error translations can also be registered on the server and given priority over standard translation. The `DBMS_SQL_TRANSLATOR.ATTR_RAISE_TRANSLATION_ERROR` attribute has the same effect on custom error translation as on query translation.

Note that the errors are translated only after a connection to the server is established. So, for errors that occur before the connection to the server is established, Error Message Translation is used.

#### Using JDBC Driver for SQL Translation

Example 4-1 demonstrates how to use a JDBC driver for SQL translation. You must first grant the `CREATE SQL TRANSLATION PROFILE` privilege to `HR` as follows:

    conn system/manager;
    grant create sql translation profile to HR;
    exit

Now, connect to the database as `HR` and execute the following SQL statements:

    drop table sample_tab;
    create table sample_tab (c1 number, c2 varchar2(100));
    insert into sample_tab values (1, 'A');
    insert into sample_tab values (1, 'A');
    insert into sample_tab values (1, 'A');
    commit;
    exec dbms_sql_translator.drop_profile('FOO');
    exec  dbms_sql_translator.create_profile('FOO');
    exec  dbms_sql_translator.register_sql_translation('FOO','select row of select c1, c2 from sample_tab
    where c1=:b1 and c2=:b2','select c1, c2 from sample_tab where c1=:b1 and c2=:b2');

Now, you can run the following program that translates SQL statements that use JDBC standard parameter markers.

Example 4-1 Translating Non-Oracle SQL Statements to Oracle SQL Dialect Using JDBC Driver

    public class SQLTransPstmt
    {
      static String url="jdbc:oracle:thin:@localhost:5521:jvx1";
      static String user="HR", pwd="hr";
      static String PROFILE = "FOO";
      static String primitiveSql = "select row of select c1, c2 from sample_tab where c1=? and c2=?";

    // Note that this query contains JDBC style parameter markers
    // But the preceding custom translation registered in SQL is using Oracle style markers

      public static void main(String[] args) throws Exception
      {
        OracleDataSource ods = new OracleDataSource();
        ods.setURL(url);

        Properties props = new Properties();
        props.put("user", user);
        props.put("password", pwd);

        // The Following connection property makes the connection translating
        props.put(OracleConnection.CONNECTION_PROPERTY_SQL_TRANSLATION_PROFILE, PROFILE);
        ods.setConnectionProperties(props);
        Connection conn = ods.getConnection();
        System.out.println("connection for SQL translation: "+conn);

        try{
          // Any statements created using a translating connection are
          // automatically translating. If you want to get a non-translating
          // statement out of a translating connection please have a look at
          // the oracle.jdbc.OracleTranslatingConnection Interface.
          // Refer to "OracleTranslatingConnection Interface"
          // for more information
          PreparedStatement trStmt = conn.prepareStatement(primitiveSql);
          trStmt.setInt(1, 1);
          trStmt.setString(2, "A");
          System.out.println("executeQuery for: "+primitiveSql);
          ResultSet trRs = trStmt.executeQuery();
          while (trRs.next())
            System.out.println("C1:"+trRs.getInt(1)+", C2:"+trRs.getString(2));
          trRs.close();

          trStmt.close();
        }catch (Exception e) {
          e.printStackTrace();
        }


        conn.close();
      }
    }

### SQL Translation of ODBC Applications

Consider the concepts necessary to understanding how to use SQL Translator with an ODBC application.

#### SQL Translation profile

For ODBC applications, the SQL Translation Profile is set at the service level. So, you do not require to set it in the `.odbc.ini` file.

#### Error Message Translation

You may prefer receiving error messages in the form of messages that used to be thrown by the native database. In such cases, when the application is set to run on Oracle Database, you must set the `SQLTranslateErrors=T` entry in the `.odbc.ini` file to translate the `ORA` errors to their native form.

#### Translating Error Messages

Example 4-2 demonstrates how to use the ODBC driver in SQL translation. The SQL statement used in the example uses Sybase `TOP N` syntax.

Note that you must set the `ServerName=` entry in the `.odbc.ini` file with the Database service name created in "[How to Use SQL Translation Framework](SQL-translation-framework-overview.md)" section. Also, set the '`SQLTranslateErros=T` entry in the `.odbc.ini` file, if you require translation of Oracle errors to native database errors.

Example 4-2 Translating Non-Oracle SQL to Oracle SQL Dialect Using ODBC Driver

    int main()
    {
     HENV m_henv;          /* environment handle */
     HDBC m_hdbc;          /* connection handle */
     HSTMT m_hstmt;        /* statement handle */
     int retCode;          /* return code */
     char dbdsn[100];      /* Initialize with the DSN name of connection */
     const  char szUID[10];/*Initialize with appropriate Username of DB */
     const char szPWD[10]; /* Initialize with appropriate Password */

     char query1[100]="select top 3 col1 from babel_tab3 order by col1";
     SQLLEN paramInd = SQL_NTS;
     SQLUINTEGER   no = 0;

     //Allocate HENV, HDBC, HSTMT handles
     retCode = SQLAllocHandle (SQL_HANDLE_ENV, SQL_NULL_HANDLE, &m_henv);
     if (retCode != SQL_SUCCESS && retCode != SQL_SUCCESS_WITH_INFO)
     {
        printf ("SQLAllocHandle failed \n");
        printSQLError (1, m_henv);
     }

     retCode = SQLSetEnvAttr (m_henv, SQL_ATTR_ODBC_VERSION, (void *) SQL_OV_ODBC3,
               SQL_IS_INTEGER);
     if (retCode != SQL_SUCCESS && retCode != SQL_SUCCESS_WITH_INFO)
     {
        printf ("SQLSetEnvAttr failed\n");
        printSQLError (1, m_henv);
     }

     retCode = SQLAllocHandle (SQL_HANDLE_DBC, m_henv, &m_hdbc);
     if (retCode != SQL_SUCCESS && retCode != SQL_SUCCESS_WITH_INFO)
     {
        printf ("SQLAllocHandle failed\n");
        printSQLError (2, m_hdbc);
     }

     retCode = SQLConnect (m_hdbc, (SQLCHAR *) dbdsn,SQL_NTS,
                           (SQLCHAR *) szUID, SQL_NTS,
                           (SQLCHAR *) szPWD, SQL_NTS);
     if (retCode != SQL_SUCCESS && retCode != SQL_SUCCESS_WITH_INFO)
     {
        printf ("SQLConnect failed to connect\n");
        printSQLError (2, m_hdbc);
     }

     retCode = SQLAllocHandle (SQL_HANDLE_STMT, m_hdbc, &m_hstmt);
     if (retCode != SQL_SUCCESS && retCode != SQL_SUCCESS_WITH_INFO)
     {
        printf ("SQLAllocHandle with SQL_HANDLE_STMT failed\n");
        printSQLError (3, m_hstmt);
     }

     /* Prepare and Execute the Sybase Top-N syntax SQL statements */

     retCode = SQLPrepare (m_hstmt, (SQLCHAR *) query1, SQL_NTS);
     if (retCode != SQL_SUCCESS && retCode != SQL_SUCCESS_WITH_INFO)
     {
        printf ("SQLPrepare failed\n");
        printSQLError (3, m_hstmt);
     }

     retCode=SQLExecute(m_hstmt);
     if (retCode != SQL_SUCCESS && retCode != SQL_SUCCESS_WITH_INFO)
     {
        printf ("SQLExecute-failed\n");
        printSQLError (3, m_hstmt);
     }

     while (retCode = SQLFetch(m_hstmt)!=SQL_NO_DATA)
     {
        retCode=SQLGetData(m_hstmt,1,SQL_C_ULONG, &no, 0, &paramInd);
        if (retCode != SQL_SUCCESS && retCode != SQL_SUCCESS_WITH_INFO)
        {
           printf ("SQLFetch failed\n");
           printSQLError (3, m_hstmt);
        }
        printf("Value is %d\n",no);
     }

     retCode = SQLCloseCursor (m_hstmt);
     if (retCode != SQL_SUCCESS && retCode != SQL_SUCCESS_WITH_INFO)
        printf ("SQLCloseCursor failed\n");

     printf ("cleanup()\n");
     retCode = SQLFreeHandle (SQL_HANDLE_STMT, m_hstmt);
     if (retCode != SQL_SUCCESS && retCode != SQL_SUCCESS_WITH_INFO)
     {
        printf ("SQLFreeHandle failed\n");
        printSQLError (3, m_hstmt);
     }

     retCode = SQLDisconnect (m_hdbc);
     if (retCode != SQL_SUCCESS && retCode != SQL_SUCCESS_WITH_INFO)
     {
        printf ("SQLDisconnect failed\n");
        printSQLError (2, m_hdbc);
     }

     retCode = SQLFreeHandle (SQL_HANDLE_DBC, m_hdbc);
     if (retCode != SQL_SUCCESS && retCode != SQL_SUCCESS_WITH_INFO)
     {
        printf ("SQLFreeHandle failed\n");
        printSQLError (2, m_hdbc);
     }

     retCode = SQLFreeHandle (SQL_HANDLE_ENV, m_henv);
     if (retCode != SQL_SUCCESS && retCode != SQL_SUCCESS_WITH_INFO)
     {
        printf ("SQLFreeHandle failed\n");
        printSQLError (1, m_henv);
     }
    }
