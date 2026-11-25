Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../AccessToken.md)
- Use
- [Tree](../package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev
- Next

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

## Uses of Interface oracle.jdbc.AccessToken

- **Packages that use [AccessToken](../AccessToken.md)**

  | Package                | Description                                                                                                                   |
  |------------------------|-------------------------------------------------------------------------------------------------------------------------------|
  | oracle.jdbc            | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`.                             |
  | oracle.jdbc.datasource | Beginning in Oracle Release 12.2, some of the Oracle extensions to JDBC are captured in the package `oracle.jdbc.datasource`. |
  | oracle.jdbc.pool       | A package of connection cache and pooling related classes.                                                                    |
  | oracle.jdbc.replay     | Provides interfaces and factory methods for Application Continuity.                                                           |

- - ### Uses of [AccessToken](../AccessToken.md) in [oracle.jdbc](../package-summary.md)

    **Methods in [oracle.jdbc](../package-summary.md) that return [AccessToken](../AccessToken.md)**

    | Modifier and Type                           | Method and Description                                                                                                                                                                                                                                                                                                     |
    |---------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`AccessToken`](../AccessToken.md) | AccessToken.[`createJsonWebToken`](../AccessToken.md)`(char[] token)`<br>Creates an `AccessToken` representing a JSON Web Token (JWT).                                                                                                                                                                                     |
    | `static `[`AccessToken`](../AccessToken.md) | AccessToken.[`createJsonWebToken`](../AccessToken.md)`(char[] token)`<br>Creates an `AccessToken` representing a JSON Web Token (JWT).                                                                                                                                                                                     |
    | `static `[`AccessToken`](../AccessToken.md) | AccessToken.[`createJsonWebToken`](../AccessToken.md)`(char[] token, `[`PrivateKey`](http://download.oracle.com/javase/8/docs/api/java/security/PrivateKey.html?is-external=true)` privateKey)`<br>Creates an `AccessToken` representing a JSON Web Token (JWT) that requires proof of possession (PoP) of a `privateKey`. |
    | `static `[`AccessToken`](../AccessToken.md) | AccessToken.[`createJsonWebToken`](../AccessToken.md)`(char[] token, `[`PrivateKey`](http://download.oracle.com/javase/8/docs/api/java/security/PrivateKey.html?is-external=true)` privateKey)`<br>Creates an `AccessToken` representing a JSON Web Token (JWT) that requires proof of possession (PoP) of a `privateKey`. |

    **Methods in [oracle.jdbc](../package-summary.md) that return types with arguments of type [AccessToken](../AccessToken.md)**

    | Modifier and Type                                                                                                                                                                          | Method and Description                                                                                                                                                                                                                                                                                                                          |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`java.util.function.Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true)`<? extends `[`AccessToken`](../AccessToken.md)`>` | AccessToken.[`createJsonWebTokenCache`](../AccessToken.md)`(`[`java.util.function.Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true)`<? extends `[`AccessToken`](../AccessToken.md)`> tokenSupplier)`<br>Returns a `Supplier` that caches access tokens generated by a `tokenSupplier`. |
    | `static `[`java.util.function.Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true)`<? extends `[`AccessToken`](../AccessToken.md)`>` | AccessToken.[`createJsonWebTokenCache`](../AccessToken.md)`(`[`java.util.function.Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true)`<? extends `[`AccessToken`](../AccessToken.md)`> tokenSupplier)`<br>Returns a `Supplier` that caches access tokens generated by a `tokenSupplier`. |

    **Methods in [oracle.jdbc](../package-summary.md) with parameters of type [AccessToken](../AccessToken.md)**

    | Modifier and Type                                          | Method and Description                                                                                                                                                                           |
    |------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OracleConnectionBuilder`](../OracleConnectionBuilder.md) | OracleConnectionBuilder.[`accessToken`](../OracleConnectionBuilder.md)`(`[`AccessToken`](../AccessToken.md)` accessToken)`<br>Specifies the `accessToken` to be used when creating a connection. |
    | [`OracleConnectionBuilder`](../OracleConnectionBuilder.md) | OracleConnectionBuilder.[`accessToken`](../OracleConnectionBuilder.md)`(`[`AccessToken`](../AccessToken.md)` accessToken)`<br>Specifies the `accessToken` to be used when creating a connection. |

    **Method parameters in [oracle.jdbc](../package-summary.md) with type arguments of type [AccessToken](../AccessToken.md)**

    | Modifier and Type                                                                                                                                                                          | Method and Description                                                                                                                                                                                                                                                                                                                          |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`java.util.function.Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true)`<? extends `[`AccessToken`](../AccessToken.md)`>` | AccessToken.[`createJsonWebTokenCache`](../AccessToken.md)`(`[`java.util.function.Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true)`<? extends `[`AccessToken`](../AccessToken.md)`> tokenSupplier)`<br>Returns a `Supplier` that caches access tokens generated by a `tokenSupplier`. |
    | `static `[`java.util.function.Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true)`<? extends `[`AccessToken`](../AccessToken.md)`>` | AccessToken.[`createJsonWebTokenCache`](../AccessToken.md)`(`[`java.util.function.Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true)`<? extends `[`AccessToken`](../AccessToken.md)`> tokenSupplier)`<br>Returns a `Supplier` that caches access tokens generated by a `tokenSupplier`. |

  - ### Uses of [AccessToken](../AccessToken.md) in [oracle.jdbc.datasource](../datasource/package-summary.md)

    **Method parameters in [oracle.jdbc.datasource](../datasource/package-summary.md) with type arguments of type [AccessToken](../AccessToken.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                                                                                                                                |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | OracleCommonDataSource.[`setTokenSupplier`](../datasource/OracleCommonDataSource.md)`(`[`java.util.function.Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true)`<? extends `[`AccessToken`](../AccessToken.md)`> tokenSupplier)`<br>Sets a supplier function that generates an access token when creating a connection with this `DataSource`. |
    | `void`            | OracleCommonDataSource.[`setTokenSupplier`](../datasource/OracleCommonDataSource.md)`(`[`java.util.function.Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true)`<? extends `[`AccessToken`](../AccessToken.md)`> tokenSupplier)`<br>Sets a supplier function that generates an access token when creating a connection with this `DataSource`. |

  - ### Uses of [AccessToken](../AccessToken.md) in [oracle.jdbc.pool](../pool/package-summary.md)

    **Fields in [oracle.jdbc.pool](../pool/package-summary.md) with type parameters of type [AccessToken](../AccessToken.md)**

    | Modifier and Type                                                                                                                                                                             | Field and Description                                                                                                                                                                      |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `protected `[`java.util.function.Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true)`<? extends `[`AccessToken`](../AccessToken.md)`>` | OracleConnectionBuilderImpl.[`tokenSupplier`](../pool/OracleConnectionBuilderImpl.md)<br>Supplier of access tokens that this builder is configured to use for authenticating a connection. |
    | `protected `[`java.util.function.Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true)`<? extends `[`AccessToken`](../AccessToken.md)`>` | OracleConnectionBuilderImpl.[`tokenSupplier`](../pool/OracleConnectionBuilderImpl.md)<br>Supplier of access tokens that this builder is configured to use for authenticating a connection. |

    **Methods in [oracle.jdbc.pool](../pool/package-summary.md) that return types with arguments of type [AccessToken](../AccessToken.md)**

    | Modifier and Type                                                                                                                                                                 | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`java.util.function.Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true)`<? extends `[`AccessToken`](../AccessToken.md)`>` | OracleConnectionBuilderImpl.[`getTokenSupplier`](../pool/OracleConnectionBuilderImpl.md)`()`<br>Returns a supplier of `AccessToken`s if one has been specified by user code calling [`OracleConnectionBuilderImpl.accessToken(AccessToken)`](../pool/OracleConnectionBuilderImpl.md), or by internal code calling [`OracleConnectionBuilderImpl.setTokenSupplier(Supplier)`](../pool/OracleConnectionBuilderImpl.md). |
    | [`java.util.function.Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true)`<? extends `[`AccessToken`](../AccessToken.md)`>` | OracleConnectionBuilderImpl.[`getTokenSupplier`](../pool/OracleConnectionBuilderImpl.md)`()`<br>Returns a supplier of `AccessToken`s if one has been specified by user code calling [`OracleConnectionBuilderImpl.accessToken(AccessToken)`](../pool/OracleConnectionBuilderImpl.md), or by internal code calling [`OracleConnectionBuilderImpl.setTokenSupplier(Supplier)`](../pool/OracleConnectionBuilderImpl.md). |

    **Methods in [oracle.jdbc.pool](../pool/package-summary.md) with parameters of type [AccessToken](../AccessToken.md)**

    | Modifier and Type                                                       | Method and Description                                                                                                                                                                                                                                                                  |
    |-------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OracleConnectionBuilderImpl`](../pool/OracleConnectionBuilderImpl.md) | OracleConnectionBuilderImpl.[`accessToken`](../pool/OracleConnectionBuilderImpl.md)`(`[`AccessToken`](../AccessToken.md)` accessToken)`<br>Sets the [`OracleConnectionBuilderImpl.accessToken(oracle.jdbc.AccessToken)`](../pool/OracleConnectionBuilderImpl.md) field of this builder. |
    | [`OracleConnectionBuilderImpl`](../pool/OracleConnectionBuilderImpl.md) | OracleConnectionBuilderImpl.[`accessToken`](../pool/OracleConnectionBuilderImpl.md)`(`[`AccessToken`](../AccessToken.md)` accessToken)`<br>Sets the [`OracleConnectionBuilderImpl.accessToken(oracle.jdbc.AccessToken)`](../pool/OracleConnectionBuilderImpl.md) field of this builder. |

    **Method parameters in [oracle.jdbc.pool](../pool/package-summary.md) with type arguments of type [AccessToken](../AccessToken.md)**

    | Modifier and Type                                                                                                  | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    |--------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `protected `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true) | OracleDataSource.[`getPhysicalConnection`](../pool/OracleDataSource.md)`(`[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` prop, `[`GSSCredential`](http://download.oracle.com/javase/8/docs/api/org/ietf/jgss/GSSCredential.html?is-external=true)` gssCredential, `[`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true)` sslContext, `[`java.util.function.Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true)`<? extends `[`AccessToken`](../AccessToken.md)`> tokenSupplier)`  |
    | `protected `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true) | OracleDataSource.[`getPhysicalConnection`](../pool/OracleDataSource.md)`(`[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` prop, `[`GSSCredential`](http://download.oracle.com/javase/8/docs/api/org/ietf/jgss/GSSCredential.html?is-external=true)` gssCredential, `[`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true)` sslContext, `[`java.util.function.Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true)`<? extends `[`AccessToken`](../AccessToken.md)`> tokenSupplier)`  |
    | `void`                                                                                                             | OracleConnectionBuilderImpl.[`setTokenSupplier`](../pool/OracleConnectionBuilderImpl.md)`(`[`java.util.function.Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true)`<? extends `[`AccessToken`](../AccessToken.md)`> tokenSupplier)`<br>Internal API to configure this builder with a [`Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true) of [`AccessToken`](../AccessToken.md)s.                                                                                                                                                        |
    | `void`                                                                                                             | OracleDataSource.[`setTokenSupplier`](../pool/OracleDataSource.md)`(`[`java.util.function.Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true)`<? extends `[`AccessToken`](../AccessToken.md)`> tokenSupplier)`                                                                                                                                                                                                                                                                                                                                                                                    |
    | `void`                                                                                                             | OracleDataSource.[`setTokenSupplier`](../pool/OracleDataSource.md)`(`[`java.util.function.Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true)`<? extends `[`AccessToken`](../AccessToken.md)`> tokenSupplier)`                                                                                                                                                                                                                                                                                                                                                                                    |
    | `void`                                                                                                             | OracleConnectionBuilderImpl.[`setTokenSupplier`](../pool/OracleConnectionBuilderImpl.md)`(`[`java.util.function.Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true)`<? extends `[`AccessToken`](../AccessToken.md)`> tokenSupplier)`<br>Internal API to configure this builder with a [`Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true) of [`AccessToken`](../AccessToken.md)s.                                                                                                                                                        |

  - ### Uses of [AccessToken](../AccessToken.md) in [oracle.jdbc.replay](../replay/package-summary.md)

    **Method parameters in [oracle.jdbc.replay](../replay/package-summary.md) with type arguments of type [AccessToken](../AccessToken.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                           |
    |-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | OracleDataSourceImpl.[`setTokenSupplier`](../replay/OracleDataSourceImpl.md)`(`[`java.util.function.Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true)`<? extends `[`AccessToken`](../AccessToken.md)`> tokenSupplier)`  |
    | `void`            | OracleDataSourceImpl.[`setTokenSupplier`](../replay/OracleDataSourceImpl.md)`(`[`java.util.function.Supplier`](http://download.oracle.com/javase/8/docs/api/java/util/function.Supplier.html?is-external=true)`<? extends `[`AccessToken`](../AccessToken.md)`> tokenSupplier)`  |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../AccessToken.md)
- Use
- [Tree](../package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev
- Next

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

Copyright © 2008, 2022, Oracle and/or its affiliates.
