Consider the APIs that are part of the `oracle.jdbc` package, specifically the elements of `oracle.jdbc` that assist in SQL translation. To successfully migrate JDBC applications, it is important to understand the translation properties, interfaces, and the error translation mechanisms.

**See Also:**

- Complete documentation of the `oracle.jdbc` package in Oracle Database JDBC Java API Reference

### Translation Properties

The translation properties are listed in Table 8-1

Table 8-1 Translation Properties

| Property                | Description                                          |
|:------------------------|:-----------------------------------------------------|
| sqlTranslationProfile   | Specifies the name of the transaction profile        |
| sqlErrorTranslationFile | Specifies the path of the SQL error translation file |

#### sqlTranslationProfile

The property `oracle.jdbc.sqlTranslationProfile` specifies the name of the transaction profile.

##### Declaration

    oracle.jdbc.sqlTranslationProfile

##### Constant

    OracleConnection.CONNECTION_PROPERTY_SQL_TRANSLATON_PROFILE

The value of the constant is `oracle.jdbc.sqlTranslationProfile`. This is also the property name.

##### Property Value

The value is a string. There is no default value.

##### Remarks

The property `sqlTranslationProfile` can be set as either a system property or a connection property. The property is required to use SQL translation. If this property is set then all statements created by the connection have SQL translation enabled unless otherwise specified.

#### sqlErrorTranslationFile

The property `oracle.jdbc.sqlErrorTranslationFile` specifies the path of the SQL error translation file.

##### Declaration

    oracle.jdbc.sqlErrorTranslationFile

##### Constant

    Oracle.connection.CONNECTION_PROPERTY_SQL_ERROR_TRANSLATION_FILE.

##### Property Value

The value is a path name. It has no default value.

##### Exceptions

An error in establishing a connection results in a SQLException but without a valid connection. However the SQL error translation file path is available either as a system property or connection property and will be used to translate the error.

##### Remarks

This file is used only for translating errors which occur when connection establishment fails. Once the connection is established this file is bypassed and is not considered even if it contains the translation details for any error which occurs after the connection is established. The property `sqlErrorTranslationFile` can be either a system property or a connection property. The content of this file is used to translate Oracle SQLExceptions into foreign SQLExceptions when there is no valid connection.

### OracleTranslatingConnection Interface

This interface is only implemented by a Connection object that supports SQL Translation. The main purpose of this interface is to get non-translating statements (including `preparedStatement` and `CallableStatement`) from a translating connection.

The public interface `oracle.jdbc.OracleTranslatingConnection` defines the factory methods for creating translating and non-translating `Statement` objects.

The `OracleTranslatingConnection` enumerations are listed in Table 8-2:

Table 8-2 OracleTranslatingConnection Enumeration

| Name                  | Description                  |
|:----------------------|:-----------------------------|
| SqlTranslationVersion | Provides the Keys to the map |

The `OracleTranslatingConnection` methods are listed in Table 8-3:

Table 8-3 OracleTranslatingConnection Methods

| Name                        | Description                                                                         |
|:----------------------------|:------------------------------------------------------------------------------------|
| createStatement()           | Creates a `Statement` object with option to translate or not translate SQL.         |
| prepareCall()               | Creates a `CallableStatement` object with option to translate or not translate SQL. |
| prepareStatement()          | Creates a `PreparedStatement` object with option to translate or not translate SQL. |
| getSQLTranslationVersions() | Returns a map of all the translation versions of the query during SQL Translation.  |

#### SqlTranslationVersion

The `SqlTranslationVersion` enumerated values specify the keys to the getSQLTranslationVersions() method.

##### Syntax

      public enum SqlTranslationVersion {
        ORIGINAL_SQL,
        JDBC_MARKER_CONVERTED,
        TRANSLATED
      }

The following table lists all the `SqlTranslationVersion` enumeration values with a description of each enumerated value.

| Member Name             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ORIGINAL_SQL`          | Specifies the original vendor specific sql                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `JDBC_MARKER_CONVERTED` | Specifies that JDBC parameter markers ('?') is replaced with Oracle style parameter markers (':b\<n\>'). Hence consecutive '?'s will be converted to `:b1`, `:b2`, `:b3` and so on. This change is required to take care of any changes in the order of parameters during translation. This version is sent to the server for translation. Hence any custom translations on the server must be registered from this version and not the `ORIGINAL_SQL` version. |
| `TRANSLATED`            | Specifies the translated query returned from the server                                                                                                                                                                                                                                                                                                                                                                                                         |

#### createStatement()

This group of methods create a `Statement` object, and specify whether the statement supports SQL translation. If the value of parameter `translating` is `TRUE`, then the returning statement supports translation and is identical to the corresponding version in the java.sql.Connection interface without the translating argument. If the value is `FALSE`, then the returning statement does not support translation.

| Syntax                                                                                                                                                                                | Description                                                                                                                   |
|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------|
| `public Statement createStatement(`<br>`  boolean translating)`<br>`throws SQLException;`                                                                                             | Creates a `Statement` object with option to translate or not translate SQL.                                                   |
| `public Statement createStatement(`<br>`  int resultSetType,  int resultSetConcurrency,  boolean translating)`<br>`throws SQLException;`                                              | Creates a `Statement` object with the given type and concurrency with option to translate or not translate SQL.               |
| `public Statement createStatement(`<br>`  int resultSetType,`<br>`  int resultSetConcurrency,`<br>`  int resultSetHoldability,`<br>`  boolean translating)`<br>`throws SQLException;` | Creates a `Statement` object with the given type, concurrency, and holdability with option to translate or not translate SQL. |

##### Parameters

| Parameter              | Description                                                             |
|:-----------------------|:------------------------------------------------------------------------|
| `resultSetType`        | Specifies the `int` value representing the result set type.             |
| `resultSetConcurrency` | Specifies the `int` value representing the result set concurrency type. |
| `resultSetHoldability` | Specifies the `int` value representing the result set holdability type. |
| `translating`          | Specifies whether or not the statement supports translation.            |

##### Return Value

The `createStatement()` method returns a `Statement` object.

##### Exceptions

The `createStatement()` method throws `SQLException`.

##### Example

Import the following packages before running the example:

    import java.sql.*;
    import java.util.Properties;

    import oracle.jdbc.OracleConnection;
    import oracle.jdbc.OracleTranslatingConnection;
    import oracle.jdbc.pool.OracleDataSource;

Run the following SQL statements:

    conn system/manager;
    grant create sql translation profile to HR;

    conn username/pwd;
    drop table sample_tab;
    create table sample_tab (c1 number, c2 varchar2(100));
    insert into sample_tab values (1, 'A');
    insert into sample_tab values (2, 'B');
    commit;
    exec dbms_sql_translator.drop_profile('FOO');
    exec  dbms_sql_translator.create_profile('FOO');
    exec  dbms_sql_translator.register_sql_translation('FOO','select row of (c1, c2) from sample_tab','select c1, c2 from sample_tab');

Example 8-1 Using the createStatement() method

    public class SQLTransStmt
    {
      static String url="jdbc:oracle:thin:@localhost:5521:orcl";
      static String user="username", pwd="pwd";
      static String PROFILE = "FOO";
      static String primitiveSql = "select row of (c1, c2) from sample_tab";

      public static void main(String[] args) throws Exception
      {
        OracleDataSource ods = new OracleDataSource();
        ods.setURL(url);

        Properties props = new Properties();
        props.put("user", user);
        props.put("password", pwd);
        props.put(OracleConnection.CONNECTION_PROPERTY_SQL_TRANSLATION_PROFILE, PROFILE);
        ods.setConnectionProperties(props);
        Connection conn = ods.getConnection();
        System.out.println("connection for SQL translation: "+conn);

        try{
          OracleTranslatingConnection trConn = (OracleTranslatingConnection) conn;
          System.out.println("Call: oracle.jdbc.OracleTranslatingConnection.createStatement(true)");
          Statement trStmt = trConn.createStatement(true);
          System.out.println("executeQuery for: "+primitiveSql);
          ResultSet trRs = trStmt.executeQuery(primitiveSql);
          while (trRs.next())
            System.out.println("C1:"+trRs.getInt(1)+", C2:"+trRs.getString(2));
          trRs.close();
          trStmt.close();
        }catch (Exception e) {
          e.printStackTrace();
        }

        try{
          OracleTranslatingConnection trConn = (OracleTranslatingConnection) conn;
          System.out.println("Call: oracle.jdbc.OracleTranslatingConnection.createStatement(false)");
          Statement trStmt = trConn.createStatement(false);
          System.out.println("executeQuery for: "+primitiveSql);
          ResultSet trRs = trStmt.executeQuery(primitiveSql);
          while (trRs.next())
            System.out.println("C1:"+trRs.getInt(1)+", C2:"+trRs.getString(2));
          trRs.close();
          trStmt.close();
        }catch (Exception e) {
          System.out.println("expected Exception: "+e.getMessage());
        }

        try{
          OracleTranslatingConnection trConn = (OracleTranslatingConnection) conn;
          System.out.println("Call: oracle.jdbc.OracleTranslatingConnection.
    createStatement(ResultSet.TYPE_SCROLL_SENSITIVE, ResultSet.CONCUR_UPDATABLE, true)");
          Statement trStmt = trConn.createStatement(ResultSet.TYPE_SCROLL_SENSITIVE, ResultSet.CONCUR_UPDATABLE, true);
          System.out.println("executeQuery for: "+primitiveSql);
          ResultSet trRs = trStmt.executeQuery(primitiveSql);
          while (trRs.next())
            System.out.println("C1:"+trRs.getInt(1)+", C2:"+trRs.getString(2));
          System.out.println("move resultset back to 2nd row...");
          trRs.absolute(2);
          while (trRs.next())
            System.out.println("C1:"+trRs.getInt(1)+", C2:"+trRs.getString(2));
          trRs.close();
          trStmt.close();
        }catch (Exception e) {
          e.printStackTrace();
        }

        try{
          conn.setAutoCommit(false);
          OracleTranslatingConnection trConn = (OracleTranslatingConnection) conn;
          System.out.println("Call: oracle.jdbc.OracleTranslatingConnection.createStatement(ResultSet.TYPE_SCROLL_SENSITIVE, ResultSet.CONCUR_UPDATABLE,
     ResultSet.HOLD_CURSORS_OVER_COMMIT, true)");
          Statement trStmt = trConn.createStatement(ResultSet.TYPE_SCROLL_SENSITIVE, ResultSet.CONCUR_UPDATABLE, ResultSet.HOLD_CURSORS_OVER_COMMIT, true);
          System.out.println("executeQuery for: "+primitiveSql);
          ResultSet trRs = trStmt.executeQuery(primitiveSql);
          trRs.last();
          System.out.println("C1:"+trRs.getInt(1)+", C2:"+trRs.getString(2));
          trRs.updateString(2, "Hello");
          trRs.updateRow();
          conn.commit();
          System.out.println("accept the update and list all of the rows again...");
          trRs.beforeFirst();
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

#### prepareCall()

This group of methods create a `CallableStatement` object, and specify whether the statement supports SQL translation. If the value of parameter `translating` is `TRUE`, then the returning statement supports translation. If the value is `FALSE`, then the returning statement does not support translation.

| Syntax                                                                                                                                                                                                       | Description                                                                                                                          |
|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------|
| `public CallableStatement prepareCall(`<br>`  String sql,`<br>`  boolean translating)`<br>`throws SQLException;`                                                                                             | Creates a `CallableStatement` object with option to translate or not translate SQL                                                   |
| `public CallableStatement prepareCall(`<br>`  String sql,`<br>`  int resultSetType,`<br>`  int resultSetConcurrency,`<br>`  boolean translating)`<br>`throws SQLException;`                                  | Creates a `CallableStatement` object with the given type and concurrency with option to translate or not translate SQL               |
| `public CallableStatement prepareCall(`<br>`  String sql,`<br>`  int resultSetType,`<br>`  int resultSetConcurrency,`<br>`  int resultSetHoldability,`<br>`  boolean translating)`<br>`throws SQLException;` | Creates a `CallableStatement` object with the given type, concurrency, and holdability with option to translate or not translate SQL |

##### Parameters

| Parameter              | Description                                                                                               |
|:-----------------------|:----------------------------------------------------------------------------------------------------------|
| `sql`                  | Specifies the `String` SQL statement value to be sent to the database; may contain one or more parameters |
| `resultSetType`        | Specifies the `int` value representing the result set type                                                |
| `resultSetConcurrency` | Specifies the `int` value representing the result set concurrency type                                    |
| `resultSetHoldability` | Specifies the `int` value representing the result set holdability type                                    |
| `translating`          | Specifies whether or not the statement supports translation                                               |

##### Return Value

The `prepareCall()` method returns a `CallableStatement` object.

##### Exceptions

The `prepareCall()` method throws `SQLException`.

##### Example

Import the following packages before running the example:

    import java.sql.*;
    import java.util.Properties;

    import oracle.jdbc.OracleConnection;
    import oracle.jdbc.OracleTranslatingConnection;
    import oracle.jdbc.pool.OracleDataSource;

Run the following SQL statements:

    conn system/manager;
    grant create sql translation profile to HR;

    conn username/pwd;

    create or replace procedure sample_proc (p_num number, p_vchar in out varchar2) AS
    begin
        p_vchar := 'p_num'||p_num||',  p_vchar'||p_vchar;
    end;
    /

    exec dbms_sql_translator.drop_profile('FOO');
    exec  dbms_sql_translator.create_profile('FOO');
    exec  dbms_sql_translator.register_sql_translation('FOO', 'exec sample_proc(:b1, :b2)', '{call sample_proc(:b1, :b2)}');

Example 8-2 Using the prepareCall() method

    public class SQLTransCstmt
    {
      static String url="jdbc:oracle:thin:@localhost:5521:orcl";
      static String user="username", pwd="pwd";
      static String PROFILE = "FOO";
      static String primitiveSql = "exec sample_proc(:b1, :b2)";

      public static void main(String[] args) throws Exception
      {
        OracleDataSource ods = new OracleDataSource();
        ods.setURL(url);

        Properties props = new Properties();
        props.put("user", user);
        props.put("password", pwd);
        props.put(OracleConnection.CONNECTION_PROPERTY_SQL_TRANSLATION_PROFILE,
          PROFILE);
        ods.setConnectionProperties(props);
        Connection conn = ods.getConnection();
        System.out.println("connection for SQL translation: "+conn);

        try{
          OracleTranslatingConnection trConn = (OracleTranslatingConnection) conn;
          System.out.println(
            "Call: oracle.jdbc.OracleTranslatingConnection.prepareCall(sql, true)");
          CallableStatement trStmt = trConn.prepareCall(primitiveSql, true);
          trStmt.setInt("b1", 1);
          trStmt.setString("b2", "A");
          trStmt.registerOutParameter("b2", Types.VARCHAR);
          System.out.println("execute for: "+primitiveSql);
          trStmt.execute();
          System.out.println("out param: "+trStmt.getString("b2"));

          trStmt.close();
        }catch (Exception e) {
          e.printStackTrace();
        }

        try{
          OracleTranslatingConnection trConn = (OracleTranslatingConnection) conn;
          System.out.println(
            "Call: oracle.jdbc.OracleTranslatingConnection.prepareCall(sql, false)");
          CallableStatement trStmt = trConn.prepareCall(primitiveSql, false);
          trStmt.setInt(1, 1);
          trStmt.setString(2, "A");
          System.out.println("execute for: "+primitiveSql);
          ResultSet trRs = trStmt.executeQuery();
          while (trRs.next())
            System.out.println("C1:"+trRs.getInt(1)+", C2:"+trRs.getString(2));
          trRs.close();

          trStmt.close();
        }catch (Exception e) {
          System.out.println("expected Exception: "+e.getMessage());
        }

        conn.close();
      }
    }

#### prepareStatement()

This group of methods create a `PreparedStatement` object, and specify whether the statement supports SQL translation. If the value of parameter `translating` is `TRUE`, then the returning statement supports translation. If the value is `FALSE`, then the returning statement does not support translation.

| Syntax                                                                                                                                                                                                                              | Description                                                                                                                          |
|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------|
| `public PreparedStatement prepareStatement(`<br>`  String sql,`<br>`  boolean translating)`<br>`throws SQLException;`                                                                                                               | Creates a `PreparedStatement` object with option to translate or not translate SQL                                                   |
| `public PreparedStatement prepareStatement(`<br>`  String sql,`<br>`  int resultSetType,`<br>`  int resultSetConcur,`<br>`  boolean translating)`<br>`throws SQLException;`                                                         | Creates a `PreparedStatement` object with the given type and concurrency with option to translate or not translate SQL               |
| `public PreparedStatement prepareStatement(`<br>`        String sql,`<br>`        int resultSetType,`<br>`        int resultSetConcur,`<br>`        int resultSetHold,`<br>`        boolean translating)`<br>`throws SQLException;` | Creates a `PreparedStatement` object with the given type, concurrency, and holdability with option to translate or not translate SQL |

| Parameter         | Description                                                                                               |
|:------------------|:----------------------------------------------------------------------------------------------------------|
| `sql`             | Specifies the `String` SQL statement value to be sent to the database; may contain one or more parameters |
| `resultSetType`   | Specifies the `int` value representing the result set type                                                |
| `resultSetConcur` | Specifies the `int` value representing the result set concurrency type                                    |
| `resultSetHold`   | Specifies the `int` value representing the result set holdability type                                    |
| `translating`     | Specifies whether or not the statement supports translation                                               |

##### Return Value

The `prepareStatement()` method returns a `PreparedStatement` object.

##### Usage Notes

When the "`?`" placeholder is used with the `prepareStatement()` method, the driver internally changes the "`?`" to Oracle-style parameters because the server side translator can only work with Oracle-style markers. This is necessary to distinguish the bind variables. If not, any change in the order of the bind variables will be indistinguishable. The replaced oracle style markers follow the format `:b<``n``>` where `<``n``>` is an incremental number. For example,` exec sample_proc(?,?)` becomes `exec sample_proc(:b1,:b2)`.

To further exemplify, consider a scenario of a vendor format where the vendor query selecting top three rows is `SELECT * FROM employees WHERE first_name=? AND employee_id=? TOP 3`. The query has to be converted to oracle dialect. In this case the following translation is to be registered on the server:

From:

    SELECT * FROM employees WHERE first_name=:b1 AND employee_id=:b2 TOP 3

To:

    SELECT * FROM employees WHERE first_name=:b1 AND employee_id=:b2 AND ROWNUM <= 3

See SqlTranslationVersion and "[SQL Translation of JDBC Applications](SQL-translation-JDBC-ODBC-applications.md)" for more information.

##### Exceptions

The `prepareStatement()` method throws `SQLException`.

##### Example

Import the following packages before running the example:

    import java.sql.*;
    import java.util.Properties;

    import oracle.jdbc.OracleConnection;
    import oracle.jdbc.OracleTranslatingConnection;
    import oracle.jdbc.pool.OracleDataSource;

Run the following SQL statements:

    conn system/manager;
    grant create sql translation profile to USER;

    conn username/pwd;
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

Example 8-3 Using the prepareStatement() method

    public class SQLTransPstmt
    {
      static String url="jdbc:oracle:thin:@localhost:5521:orcl";
      static String user="username", pwd="pwd";
      static String PROFILE = "FOO";
      static String primitiveSql = "select row of select c1, c2 from sample_tab
        where c1=:b1 and c2=:b2";

      public static void main(String[] args) throws Exception
      {
        OracleDataSource ods = new OracleDataSource();
        ods.setURL(url);

        Properties props = new Properties();
        props.put("user", user);
        props.put("password", pwd);
        props.put(OracleConnection.CONNECTION_PROPERTY_SQL_TRANSLATION_PROFILE,
          PROFILE);
        ods.setConnectionProperties(props);
        Connection conn = ods.getConnection();
        System.out.println("connection for SQL translation: "+conn);

        try{
          OracleTranslatingConnection trConn = (OracleTranslatingConnection) conn;
          System.out.println("Call:
            oracle.jdbc.OracleTranslatingConnection.prepareStatement(sql, true)");
          PreparedStatement trStmt = trConn.prepareStatement(primitiveSql, true);
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

        try{
          OracleTranslatingConnection trConn = (OracleTranslatingConnection) conn;
          System.out.println("Call:
            oracle.jdbc.OracleTranslatingConnection.prepareStatement(sql, false)");
          PreparedStatement trStmt = trConn.prepareStatement(primitiveSql, false);
          trStmt.setInt(1, 1);
          trStmt.setString(2, "A");
          System.out.println("executeQuery for: "+primitiveSql);
          ResultSet trRs = trStmt.executeQuery();
          while (trRs.next())
            System.out.println("C1:"+trRs.getInt(1)+", C2:"+trRs.getString(2));
          trRs.close();

          trStmt.close();
        }catch (Exception e) {
        System.out.println("expected Exception: "+e.getMessage());
        }

        try{
          OracleTranslatingConnection trConn = (OracleTranslatingConnection) conn;
          System.out.println("Call:
            oracle.jdbc.OracleTranslatingConnection.prepareStatement(
            sql, ResultSet.TYPE_SCROLL_SENSITIVE, ResultSet.CONCUR_UPDATABLE, true)");
          PreparedStatement trStmt = trConn.prepareStatement(
            primitiveSql, ResultSet.TYPE_SCROLL_SENSITIVE,
            ResultSet.CONCUR_READ_ONLY, true);
          trStmt.setInt(1, 1);
          trStmt.setString(2, "A");
          System.out.println("executeQuery for: "+primitiveSql);
          ResultSet trRs = trStmt.executeQuery();
          while (trRs.next())
            System.out.println("C1:"+trRs.getInt(1)+", C2:"+trRs.getString(2));

          System.out.println("trRs.beforeFirst and show resultSet again...");
          trRs.beforeFirst();
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

#### getSQLTranslationVersions()

Returns a map of all the translation versions of the query during SQL Translation. In case of an exception, and if `suppressExceptions` is true, then the translated version in the map is `NULL`.

##### Syntax

    public Map<SqlTranslationVersion, String> getSqlTranslationVersions(
      String sql,
      boolean suppressExceptions)
    throws SQL Exception;

##### Return Value

Map with all translation versions of a query. See SqlTranslationVersion `enum` for more details about returning versions.

##### Exception

This method throws `SQLException` if there is a problem in query translation, provided `suppressExceptions` is false.

### Error Translation Configuration File

An XML configuration file (path) is provided as a value of the `oracle.jdbc.sqlErrorTranslationFile` property. This file contains the translations information for errors. These errors occur when a connection to the server cannot be established and thus translation cannot happen on the server. Error messages are of the type that define the state of the database that prevents the connection from being established.

The structure of the configuration XML file is defined in the DTD as follows:

    <!DOCTYPE LocalTranslationProfile[

    <!ELEMENT LocalTranslationProfile (Exception+)>
    <!ELEMENT Exception (ORAError, ErrorCode, SQLState )>
    <!ELEMENT ORAError (#PCDATA)>
    <!ELEMENT ErrorCode (#PCDATA)>
    <!ELEMENT SQLState (#PCDATA)>
    ]>

where,

- `ORAError` is an `int` value and specifies the error code for the oracle error.

- `ErrorCode` is an `int` value and specifies the vendor error code, that is, the translated code.

- `SQLState` is a `String` value and specifies the vendor SQL state.
