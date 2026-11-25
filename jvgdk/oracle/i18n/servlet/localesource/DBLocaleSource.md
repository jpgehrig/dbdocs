Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database Globalization Development Kit Java API Reference
19c**
E96350-01

- [Prev Class](ApplicationDefault.md)
- [Next Class](HttpAcceptLanguage.md)

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

oracle.i18n.servlet.localesource

## Class DBLocaleSource

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.i18n.servlet.localesource.LocaleSource](LocaleSource.md)

  - - oracle.i18n.servlet.localesource.DBLocaleSource

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://docs.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true)

  ------------------------------------------------------------------------



      public class DBLocaleSource
      extends LocaleSource

  The `DBLocaleSource` class is the predefined database locale source that accesses a user profile table including user locale preferences. All user profile information can be specified in the GDK application configuration file. Default caching: This locale source is cached in the session by default
  The database locale source should use the special tag `<db-locale-source>` to include the user profile information in the list of the locale determination rules. The following attributes are required:

  - `data-source-name`: the data source name that must be included in the data source definition file. For example, `data-sources.xml` is used for the data source in OC4J. All authentication information should be included in the data sources.
  - `locale-source-table`: the name, optionally qualified with a schema name, of the table that contains the users' locale preferences.
  - `user-column`: the name of the column in the locale source table that identifies the user for whom the given table row contains locale preference. Usually, the column contains user IDs, such as e-mail addresses, login names, etc. **Note:** The values in this column are compared case-insensitively.
  - `user-key`: the name of the key used in the session object of the JSP/Java Servlet application to identify the current authenticated user. If the value for the key is not `null`, it is used to case-insensitively match the value in the `user-column` to find the user's locale preference. Otherwise the GDK assumes that no user is authenticated and DBLocaleSource cannot used.

  The attributes for the locale must be specified in one of the following parameters depending on the scenario:

  Scenario 1: If the user locale preference is stored in the form of ISO locale, use:

  - `locale-column`: the column that includes the ISO locale

  Scenario 2: If the user locale preference is stored in the form of Oracle language and Oracle territory names, use:

  - `language-column`: the column that includes the Oracle language name. This takes precedence over the value in `locale-column`.
  - `territory-column`: the column that includes the Oracle territory name. This takes precedence over the value in `locale-column`.

  Scenario 3: If the user locale preference is stored in the form of Oracle abbreviation language and territory names, use:

  - `short-language-column`: the column that includes the abbreviation of the Oracle language name. If both `language-column` and `short-language-column` are specified, `language-column` takes precedence.
  - `territory-column`: the column that includes the Oracle territory name. This takes precedence over the value in `locale-column`.

  Additionally, the following attributes may be specified:

  - `charset-column`: the column that includes the Oracle character set for the client. Note this is not the page character set information.
  - `timezone-column`: the column that includes the time zone ID.
  - `linguistic-sort-column`: the column that includes the Oracle linguistic sorting name.
  - `date-format-column`: the column that includes the short date format mask.
  - `long-date-format-column`: the column that includes the long date format mask.
  - `time-format-column`: the column that includes the time format mask.
  - `date-time-format-column`: the column that includes the short date and time format mask.
  - `long-date-time-format-column`: the column that includes the long date and time format mask.
  - `number-format-column`: the column that includes the number format mask.
  - `currency-format-column`: the column that includes the currency format mask.
  - `writing-direction-column`: the column that includes the writing direction, either `LTR` or `RTL`.
  - `iso-currency-column`: the column that includes the ISO 4217 currency ID.
  - `diagnostics-level`: sets the amount of diagnostics information logged in the servlet log. The servlet log is the log that the servlet container provides for the Java EE javax.servlet.ServletContext.log() method. If `diagnostics-level` is set to "0" (default), nothing is logged. If it is set to "1", locale source configuration errors are logged. If it is set to "2", errors in the retrieved DB data are logged as well. Level "3" is reserved for tracing. The behavior for any other value is currently undefined. In a production environment, set the level low to prevent malicious requests from flooding the log file.

  The locale source table name and all column names must be either double-quoted or unquoted SQL identifiers. Double-quoted identifiers are used verbatim. Unquoted identifiers are converted to uppercase and double-quoted before use. The locale source table name may be prefixed with a schema name, which follows the same quoting rules.

  The quoting discussed here pertains to attribute values after they have been retrieved from the XML configuration file, that is, after any XML escaping and quoting has already been interpreted and removed. Also, any character with the Unicode code point U+0020 or less is stripped from the beginning and end of the XML attribute value and from around the period separating schema and table name before the value is interpreted as an SQL identifier.

  For example, if the configuration file contains:

      locale-source-table="app . user_profiles"

  then the table name is treated as the schema-qualified unquoted identifier `app.user_profiles` and it is used as follows:

      SELECT ... FROM "APP"."USER_PROFILES";

  However, if the configuration file contains:

      locale-source-table='"user profiles"'

  or

      locale-source-table="&quot;user profiles&quot;"

  then the table name is treated as the quoted identifier `"user profiles"` and it is used as follows:

      SELECT ... FROM "user profiles";

  Example: Let's assume that the user locale and time zone preferences are used for globalized operations and the user schema table is specified as follows:

       create table user_profile
       (
         userid varchar2(100) primary key, -- user id
         ... (various user information)
         locale  varchar2(10), -- user locale preference, e.g., ja-JP
         timezone varchar2(50) -- user time zone preference,
                                  e.g., America/Los_Angeles
       )


  Let the data source file contain the following connection information:

       <data-source class="com.evermind.sql.DriverManagerDataSource"
         name="OracleDS"
         location="jdbc/OracleCoreDS"
         xa-location="jdbc/xa/OracleXADS"
         ejb-location="jdbc/OracleDS"
         connection-driver="oracle.jdbc.driver.OracleDriver"
         username="yourapp"
         password="<db password>"
         url="jdbc:oracle:thin:@localhost:1521:orcl"
         inactivity-timeout="30"
         />


  Also, the application provides an authentication filter that sets `"userinfo"` to either the user id or `null` in the session object so that the database locale source object can determine if the user is authenticated or not.

  In such case, the locale determination rule should be specified as follows:

       <locale-determine-rule>
         <db-locale-source
          data-source-name="jdbc/OracleCoreDS"
          locale-source-table="user_profiles"
          user-key="userinfo"
          user-column="userid"
          locale-column="locale"
          timezone-column="timezone"
        >oracle.i18n.servlet.localesource.DBLocaleSource</db-locale-source>
        <locale-source>oracle.i18n.servlet.localesource.HttpAcceptLanguage</locale-source>
       </locale-determine-rule>


  Since:
  10.1.0.2

  See Also:
  [Serialized Form](../../../../serialized-form.md)

<!-- -->

- - ### Nested Class Summary

    - ### Nested classes/interfaces inherited from class oracle.i18n.servlet.localesource.[LocaleSource](LocaleSource.md)

      [`LocaleSource.Alignment`](LocaleSource.Alignment.md)`, `[`LocaleSource.Parameter`](LocaleSource.Parameter.md)`, `[`LocaleSource.WritingDirection`](LocaleSource.WritingDirection.md)

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class oracle.i18n.servlet.localesource.[LocaleSource](LocaleSource.md)

      [`equals`](LocaleSource.md)`, `[`getAttribute`](LocaleSource.md)`, `[`getCharacterSet`](LocaleSource.md)`, `[`getCollator`](LocaleSource.md)`, `[`getCurrencyFormat`](LocaleSource.md)`, `[`getDateFormat`](LocaleSource.md)`, `[`getDateTimeFormat`](LocaleSource.md)`, `[`getISOCurrency`](LocaleSource.md)`, `[`getLocale`](LocaleSource.md)`, `[`getLocaleSourceClass`](LocaleSource.md)`, `[`getNumberFormat`](LocaleSource.md)`, `[`getTimeFormat`](LocaleSource.md)`, `[`getTimeZone`](LocaleSource.md)`, `[`getWritingDirection`](LocaleSource.md)`, `[`hashCode`](LocaleSource.md)`, `[`isCached`](LocaleSource.md)`, `[`isReadOnly`](LocaleSource.md)`, `[`load`](LocaleSource.md)`, `[`setAttribute`](LocaleSource.md)`, `[`setCharacterSet`](LocaleSource.md)`, `[`setCollator`](LocaleSource.md)`, `[`setCurrencyFormat`](LocaleSource.md)`, `[`setDateFormat`](LocaleSource.md)`, `[`setDateTimeFormat`](LocaleSource.md)`, `[`setISOCurrency`](LocaleSource.md)`, `[`setLocale`](LocaleSource.md)`, `[`setLocale`](LocaleSource.md)`, `[`setLocaleSourceClass`](LocaleSource.md)`, `[`setNumberFormat`](LocaleSource.md)`, `[`setTimeFormat`](LocaleSource.md)`, `[`setTimeZone`](LocaleSource.md)`, `[`setWritingDirection`](LocaleSource.md)`, `[`store`](LocaleSource.md)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database Globalization Development Kit Java API Reference
19c**
E96350-01

- [Prev Class](ApplicationDefault.md)
- [Next Class](HttpAcceptLanguage.md)

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

Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
