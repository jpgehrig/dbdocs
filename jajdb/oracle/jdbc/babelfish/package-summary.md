Skip navigation links

- [Overview](../../../overview-summary.md)
- Package
- Class
- [Use](package-use.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Package](../aq/package-summary.md)
- [Next Package](../datasource/package-summary.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

# Package oracle.jdbc.babelfish

Provides the classes necessary for the support for application migration feature.

See: Description

- **Class Summary**

  | Class                                                       | Description                                                                                                       |
  |-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------|
  | [BabelfishCallableStatement](BabelfishCallableStatement.md) | Proxy Superclass for java.sql.CallableStatement interface.                                                        |
  | [BabelfishConnection](BabelfishConnection.md)               | Proxy Superclass for java.sql.Connection interface.                                                               |
  | [BabelfishGenericProxy](BabelfishGenericProxy.md)           | Defines the common behavior needed by all the babelfish proxies to support auto translation of queries or errors. |
  | [BabelfishPreparedStatement](BabelfishPreparedStatement.md) | Proxy Superclass for java.sql.PreparedStatement interface.                                                        |
  | [BabelfishStatement](BabelfishStatement.md)                 | Proxy Superclass for java.sql.Statement interface.                                                                |
  | [TranslationManager](TranslationManager.md)                 | Provides the translator for a connection.                                                                         |
  | [Translator](Translator.md)                                 | Translates queries and errors.                                                                                    |

## Package oracle.jdbc.babelfish Description

Provides the classes necessary for the support for application migration feature. It enables non-oracle dialect queries to be run with Oracle Database by auto-translating the queries and errors internally.

On activation of the feature the driver goes through this package and automatically proxyfies all the required objects to support for auto translation of queries from other dialects to oracle dialect and vice versa for error codes based on the translation profile. Except for setting the connection properties to activate the feature, for the most part this package's functionality is intended to be transparent to the user so that there is minimal changes required to existing user code.

The following properties are required

- **oracle.jdbc.sqlTranslationProfile** - The string identifier for the translation profile or the translator to be used. Presence of this property activates the support for SQL Translation and is thus mandatory if SQL Translation feature is required.
- **oracle.jdbc.sqlErrorTranslationFile** - Path to an xml file which provides the Error code translations for those errors which occur if a connection can not be established to the server. The XML file is to be provided by the user and must conform to the following DTD. This is an optional property and if not provided then untranslated exceptions with oracle error codes are thrown. This property only affects the exceptions which happen when a connection to the server cannot be established. Once connection is established the translation happens on the server bypassing the local error translation file.

<!-- -->

    <!DOCTYPE LocalTranslationProfile[
    <!ELEMENT LocalTranslationProfile (Exception+)>
    <!ELEMENT Exception (ORAError, ErrorCode, SQLState )>
    <!ELEMENT ORAError (#PCDATA)>
    <!ELEMENT ErrorCode (#PCDATA)>
    <!ELEMENT SQLState (#PCDATA)>
    ]>



Since:
12*c*

Skip navigation links

- [Overview](../../../overview-summary.md)
- Package
- Class
- [Use](package-use.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Package](../aq/package-summary.md)
- [Next Package](../datasource/package-summary.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

Copyright © 2008, 2022, Oracle and/or its affiliates.
