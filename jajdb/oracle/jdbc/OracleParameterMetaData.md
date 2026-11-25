Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleParameterMetaData.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleOpaque.md)
- [Next Class](OraclePooledConnectionBuilder.md)

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

## Interface OracleParameterMetaData

- All Superinterfaces:
  [ParameterMetaData](http://download.oracle.com/javase/8/docs/api/java/sql/ParameterMetaData.html?is-external=true), [Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true)

  ------------------------------------------------------------------------



      public interface OracleParameterMetaData
      extends ParameterMetaData

  This interface defines the Oracle extensions to the standard JDBC interface `java.sql.ParameterMetaData`. For pre-JDK 1.4 applications, this interface provides the equivalent functions in `java.sql.ParameterMetaData`. Applications can use `java.sql.ParameterMetaData` where they do not make use of Oracle extensions. However, when an application uses the Oracle extensions to `java.sql.ParameterMetaData`, it must use `oracle.jdbc.OracleParameterMetaData`.
  This is an interface that can be used to get information about the types and properties of the parameters in a `PreparedStatement` object.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface java.sql.[ParameterMetaData](http://download.oracle.com/javase/8/docs/api/java/sql/ParameterMetaData.html?is-external=true)

      [`parameterModeIn`](http://download.oracle.com/javase/8/docs/api/java/sql/ParameterMetaData.html?is-external=true#parameterModeIn)`, `[`parameterModeInOut`](http://download.oracle.com/javase/8/docs/api/java/sql/ParameterMetaData.html?is-external=true#parameterModeInOut)`, `[`parameterModeOut`](http://download.oracle.com/javase/8/docs/api/java/sql/ParameterMetaData.html?is-external=true#parameterModeOut)`, `[`parameterModeUnknown`](http://download.oracle.com/javase/8/docs/api/java/sql/ParameterMetaData.html?is-external=true#parameterModeUnknown)`, `[`parameterNoNulls`](http://download.oracle.com/javase/8/docs/api/java/sql/ParameterMetaData.html?is-external=true#parameterNoNulls)`, `[`parameterNullable`](http://download.oracle.com/javase/8/docs/api/java/sql/ParameterMetaData.html?is-external=true#parameterNullable)`, `[`parameterNullableUnknown`](http://download.oracle.com/javase/8/docs/api/java/sql/ParameterMetaData.html?is-external=true#parameterNullableUnknown)

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from interface java.sql.[ParameterMetaData](http://download.oracle.com/javase/8/docs/api/java/sql/ParameterMetaData.html?is-external=true)

      [`getParameterClassName`](http://download.oracle.com/javase/8/docs/api/java/sql/ParameterMetaData.html?is-external=true#getParameterClassName_int_)`, `[`getParameterCount`](http://download.oracle.com/javase/8/docs/api/java/sql/ParameterMetaData.html?is-external=true#getParameterCount__)`, `[`getParameterMode`](http://download.oracle.com/javase/8/docs/api/java/sql/ParameterMetaData.html?is-external=true#getParameterMode_int_)`, `[`getParameterType`](http://download.oracle.com/javase/8/docs/api/java/sql/ParameterMetaData.html?is-external=true#getParameterType_int_)`, `[`getParameterTypeName`](http://download.oracle.com/javase/8/docs/api/java/sql/ParameterMetaData.html?is-external=true#getParameterTypeName_int_)`, `[`getPrecision`](http://download.oracle.com/javase/8/docs/api/java/sql/ParameterMetaData.html?is-external=true#getPrecision_int_)`, `[`getScale`](http://download.oracle.com/javase/8/docs/api/java/sql/ParameterMetaData.html?is-external=true#getScale_int_)`, `[`isNullable`](http://download.oracle.com/javase/8/docs/api/java/sql/ParameterMetaData.html?is-external=true#isNullable_int_)`, `[`isSigned`](http://download.oracle.com/javase/8/docs/api/java/sql/ParameterMetaData.html?is-external=true#isSigned_int_)

    <!-- -->

    - ### Methods inherited from interface java.sql.[Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true)

      [`isWrapperFor`](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true#isWrapperFor_java_lang_Class_)`, `[`unwrap`](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true#unwrap_java_lang_Class_)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleParameterMetaData.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleOpaque.md)
- [Next Class](OraclePooledConnectionBuilder.md)

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
