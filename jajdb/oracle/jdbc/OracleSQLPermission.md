Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleSQLPermission.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleShardingKeyBuilder.md)
- [Next Class](OracleStatement.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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

oracle.jdbc

## Class OracleSQLPermission

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [java.security.Permission](http://download.oracle.com/javase/8/docs/api/java/security/Permission.html?is-external=true)

  - - [java.security.BasicPermission](http://download.oracle.com/javase/8/docs/api/java/security/BasicPermission.html?is-external=true)

    - - oracle.jdbc.OracleSQLPermission

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), [Guard](http://download.oracle.com/javase/8/docs/api/java/security/Guard.html?is-external=true)

  ------------------------------------------------------------------------



      public final class OracleSQLPermission
      extends BasicPermission

  The Permission class for Java security permissions unique to the Oracle JDBC drivers. As of this release the only supported target is "callAbort". The actions are ignored.
  Since:
  release specific (what release of product did this appear in)

  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                 |
    |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `OracleSQLPermission``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name)`                                                                                                             |
    | `OracleSQLPermission``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` actions)`  |

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class java.security.[BasicPermission](http://download.oracle.com/javase/8/docs/api/java/security/BasicPermission.html?is-external=true)

      [`equals`](http://download.oracle.com/javase/8/docs/api/java/security/BasicPermission.html?is-external=true#equals_java_lang_Object_)`, `[`getActions`](http://download.oracle.com/javase/8/docs/api/java/security/BasicPermission.html?is-external=true#getActions__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/security/BasicPermission.html?is-external=true#hashCode__)`, `[`implies`](http://download.oracle.com/javase/8/docs/api/java/security/BasicPermission.html?is-external=true#implies_java_security_Permission_)`, `[`newPermissionCollection`](http://download.oracle.com/javase/8/docs/api/java/security/BasicPermission.html?is-external=true#newPermissionCollection__)

    <!-- -->

    - ### Methods inherited from class java.security.[Permission](http://download.oracle.com/javase/8/docs/api/java/security/Permission.html?is-external=true)

      [`checkGuard`](http://download.oracle.com/javase/8/docs/api/java/security/Permission.html?is-external=true#checkGuard_java_lang_Object_)`, `[`getName`](http://download.oracle.com/javase/8/docs/api/java/security/Permission.html?is-external=true#getName__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/security/Permission.html?is-external=true#toString__)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Constructor Detail

    - #### OracleSQLPermission

          public OracleSQLPermission(String name)

    <!-- -->

    - #### OracleSQLPermission

          public OracleSQLPermission(String name,
                                     String actions)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleSQLPermission.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleShardingKeyBuilder.md)
- [Next Class](OracleStatement.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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

Copyright © 2008, 2022, Oracle and/or its affiliates.
