Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev Class](SyntaxException.md)
- [Next Class](SyntaxObjectVisitor.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

oracle.olapi.syntax

## Class SyntaxObject

- java.lang.Object

- - oracle.olapi.syntax.SyntaxObject

<!-- -->

- Direct Known Subclasses:
  [AggregateOverClause](AggregateOverClause.md), [AggregationCase](AggregationCase.md), [BuildCommand](BuildCommand.md), [BuildItem](BuildItem.md), [BuildProcess](BuildProcess.md), [BuildSpecification](BuildSpecification.md), [ConsistentSolveSpecification](ConsistentSolveSpecification.md), [DataObject](DataObject.md), [SQLDataType](SQLDataType.md), [SymmetricCondition](SymmetricCondition.md), [SymmetricConditionElement](SymmetricConditionElement.md)

  ------------------------------------------------------------------------



      public abstract class SyntaxObject
      extends java.lang.Object

  An abstract base class for objects that specify tables or columns in an Oracle Database instance, and that represent selections of data and operations on the data. A `SyntaxObject` has static methods that construct a `SyntaxObject` from text in the expression syntax of the Oracle OLAP Java API. The expression syntax of the API is very similar to the SQL expression syntax. A `SyntaxObject` also has methods that convert the `SyntaxObject` into a textual representation in the expression syntax.
  An application can create a `SyntaxObject` by using a `fromSyntax` method. It can also explicity create some subclasses of `SyntaxObject` by using a constructor method of the subclass or implicitly create other subclasses by using a method that returns a `SyntaxObject`. For example, the following code creates a `StringExpression` using a `fromSyntax` method, another `StringExpression` using a constructor method, and a `Query` using a method that returns a `Query`.

       // mp is the MdmMetadataProvider for the session.
       // The expression syntax requires that a string literal be enclosed
       // in single quotation marks.
       StringExpression exp = (StringExpression)
                    SyntaxObject.fromSyntax("'Hello world from syntax.'", mp);
       StringExpression strExp =
                    new StringExpression("Hello world using constructor.");
       System.out.println(exp.getValue());
       System.out.println(strExp.getValue());

       // prodTable is the MdmTable for the Products dimension.
       Query query = prodTable.getQuery();

  The output of the example is the following.
       Hello world from syntax.
       Hello world using constructor.

<!-- -->

- - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type           | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    |-----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                   | `equals``(SyntaxObject synObject)`<br>Performs a case-sensitive comparison between the string representation of the specified `SyntaxObject` and that of this `SyntaxObject`.                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `boolean`                   | `equals``(SyntaxObject synObject, boolean bIgnorecase)`<br>Compares the string representation of the specified `SyntaxObject` with that of this `SyntaxObject`.                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static SyntaxObject`       | `fromSyntax``(java.lang.String syntax, `[`MdmMetadataProvider`](../metadata/mdm/MdmMetadataProvider.md)` metadataProvider)`<br>Creates a `SyntaxObject` from a string in expression syntax.                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static SyntaxObject`       | `fromSyntax``(java.lang.String syntax, `[`MdmMetadataProvider`](../metadata/mdm/MdmMetadataProvider.md)` metadataProvider, java.lang.String owner)`<br>Creates a `SyntaxObject` from a string in expression syntax and provides an owner for the `SyntaxObject`.                                                                                                                                                                                                                                                                                                                             |
    | `static SyntaxObject`       | `fromSyntax``(java.lang.String syntax, `[`MdmMetadataProvider`](../metadata/mdm/MdmMetadataProvider.md)` metadataProvider, java.lang.String owner, boolean isForQuery)`<br>Creates a `SyntaxObject` from a string in expression syntax, provides an owner for the `SyntaxObject`, and indicates whether the `SyntaxObject` is a `Query`.                                                                                                                                                                                                                                                     |
    | `static SyntaxObject`       | `fromSyntax``(java.lang.String syntax, `[`MdmMetadataProvider`](../metadata/mdm/MdmMetadataProvider.md)` metadataProvider, java.lang.String owner, boolean isForQuery, java.util.List<`[`Query`](Query.md)`> queries)`<br>Creates a `SyntaxObject` from a string in expression syntax, provides an owner for the `SyntaxObject`, indicates whether the `SyntaxObject` is a `Query`, and provides the `Query` objects that are referenced by the expression.                                                                                                                                  |
    | `static SyntaxObject`       | `fromSyntax``(java.lang.String syntax, `[`MdmMetadataProvider`](../metadata/mdm/MdmMetadataProvider.md)` metadataProvider, java.lang.String owner, boolean isForQuery, java.util.List<`[`Query`](Query.md)`> queries, `[`XMLParserCallback`](../metadata/XMLParserCallback.md)` errorCallback)`<br>Creates a `SyntaxObject` from a string in expression syntax supplied by a `Reader`, provides an owner for the `SyntaxObject`, indicates whether the `SyntaxObject` is a `Query`, provides the `Query` objects that are referenced by the expression, and provides an `XMLParserCallback`. |
    | `boolean`                   | `isValid``()`<br>Indicates whether the `SyntaxObject` has any `UnresolvedMetadataObjectReference` objects associated with it.                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `java.lang.String`          | `toSyntax``()`<br>Converts the `SyntaxObject` into a textual representation in the expression syntax.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `java.lang.String`          | `toSyntax``(java.lang.String owner)`<br>Converts the `SyntaxObject` into a textual representation in the expression syntax and provides the owner of the `SyntaxObject`.                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `void`                      | `toSyntax``(java.lang.StringBuffer buffer, java.lang.String owner, java.util.List<`[`Query`](Query.md)`> queries)`<br>Converts the `SyntaxObject` into a textual representation in the expression syntax, provides the owner of the `SyntaxObject` separately, and provides the `Query` objects that are referenced in the `SyntaxObject`.                                                                                                                                                                                                                                                   |
    | `void`                      | `toSyntax``(java.lang.StringBuffer buffer, java.lang.String owner, java.util.List<`[`Query`](Query.md)`> queries, boolean suppressNamespace)`<br>Converts the `SyntaxObject` into a textual representation in the expression syntax, provides the owner of the `SyntaxObject` separately, and provides the `Query` objects that are referenced in the `SyntaxObject`.                                                                                                                                                                                                                        |
    | `java.lang.String`          | `toSyntax``(java.lang.String owner, java.util.List<`[`Query`](Query.md)`> queries)`<br>Converts the `SyntaxObject` into a textual representation in the expression syntax, provides the owner of the `SyntaxObject` separately, and provides the `Query` objects that are referenced in the `SyntaxObject`.                                                                                                                                                                                                                                                                                  |
    | `java.lang.String`          | `toSyntax``(java.lang.String owner, `[`Query`](Query.md)` query)`<br>Converts the `SyntaxObject` into a textual representation in the expression syntax, provides the owner of the `SyntaxObject` separately, and provides the `Query` that is referenced in the `SyntaxObject`.                                                                                                                                                                                                                                                                                                             |
    | `abstract java.lang.Object` | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the appropriate method of a `SyntaxObjectVisitor` and passes that method the `SyntaxObject` and an `Object`.                                                                                                                                                                                                                                                                                                                                                                         |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### visit

          public abstract java.lang.Object visit(SyntaxObjectVisitor visitor,
                                                 java.lang.Object context)

      Calls the appropriate method of a `SyntaxObjectVisitor` and passes that method the `SyntaxObject` and an `Object`.
      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitClearCommand` method.

    <!-- -->

    - #### toSyntax

          public final java.lang.String toSyntax()

      Converts the `SyntaxObject` into a textual representation in the expression syntax.
      Returns:
      A `String` that contains the expression for the `SyntaxObject`.

    <!-- -->

    - #### toSyntax

          public final java.lang.String toSyntax(java.lang.String owner)

      Converts the `SyntaxObject` into a textual representation in the expression syntax and provides the owner of the `SyntaxObject`.
      Parameters:
      `owner` - A `String` that is the name of the `MdmDatabaseSchema` that owns the `SyntaxObject`.

      Returns:
      A `String` that contains the expression for the `SyntaxObject`.

    <!-- -->

    - #### toSyntax

          public final java.lang.String toSyntax(java.lang.String owner,
                                                 Query query)

      Converts the `SyntaxObject` into a textual representation in the expression syntax, provides the owner of the `SyntaxObject` separately, and provides the `Query` that is referenced in the `SyntaxObject`.
      Parameters:
      `owner` - A `String` that is the name of the `MdmDatabaseSchema` that owns the `SyntaxObject`.

      `query` - The `Query` that is referenced in the `SyntaxObject`.

      Returns:
      A `String` that contains the expression for the `SyntaxObject`.

    <!-- -->

    - #### toSyntax

          public final java.lang.String toSyntax(java.lang.String owner,
                                                 java.util.List<Query> queries)

      Converts the `SyntaxObject` into a textual representation in the expression syntax, provides the owner of the `SyntaxObject` separately, and provides the `Query` objects that are referenced in the `SyntaxObject`.
      Parameters:
      `owner` - A `String` that is the name of the `MdmDatabaseSchema` that owns the `SyntaxObject`.

      `queries` - A `List` of `Query` objects referenced in the `SyntaxObject`.

      Returns:
      A `String` that contains the expression for the `SyntaxObject`.

    <!-- -->

    - #### toSyntax

          public final void toSyntax(java.lang.StringBuffer buffer,
                                     java.lang.String owner,
                                     java.util.List<Query> queries)

      Converts the `SyntaxObject` into a textual representation in the expression syntax, provides the owner of the `SyntaxObject` separately, and provides the `Query` objects that are referenced in the `SyntaxObject`.
      Parameters:
      `buffer` - A `StringBuffer` that this method uses in parsing the expression.

      `owner` - A `String` that is the name of the `MdmDatabaseSchema` that owns the `SyntaxObject`.

      `queries` - A `List` of `Query` objects referenced in the `SyntaxObject`.

    <!-- -->

    - #### toSyntax

          public final void toSyntax(java.lang.StringBuffer buffer,
                                     java.lang.String owner,
                                     java.util.List<Query> queries,
                                     boolean suppressNamespace)

      Converts the `SyntaxObject` into a textual representation in the expression syntax, provides the owner of the `SyntaxObject` separately, and provides the `Query` objects that are referenced in the `SyntaxObject`.
      Parameters:
      `buffer` - A `StringBuffer` that this method uses in parsing the expression.

      `owner` - A `String` that is the name of the `MdmDatabaseSchema` that owns the `SyntaxObject`.

      `queries` - A `List` of `Query` objects referenced in the `SyntaxObject`.

      `suppressNamespace` - If `true`, namespaces are not printed for objects referenced in the `SyntaxObject`. If `false` (the default), namespaces are printed for all objects that are not in the default namespace.

    <!-- -->

    - #### fromSyntax

          public static SyntaxObject fromSyntax(java.lang.String syntax,
                                                MdmMetadataProvider metadataProvider)

      Creates a `SyntaxObject` from a string in expression syntax.
      Parameters:
      `syntax` - A `String` that contains the expression that specifies a `SyntaxObject`.

      `metadataProvider` - The `MdmMetadataProvider` for the current session.

      Returns:
      A `SyntaxObject`.

    <!-- -->

    - #### fromSyntax

          public static SyntaxObject fromSyntax(java.lang.String syntax,
                                                MdmMetadataProvider metadataProvider,
                                                java.lang.String owner)

      Creates a `SyntaxObject` from a string in expression syntax and provides an owner for the `SyntaxObject`.
      Parameters:
      `syntax` - A `String` that contains the expression that specifies a `SyntaxObject`.

      `metadataProvider` - The `MdmMetadataProvider` for the current session.

      `owner` - A `String` that is the name of the `MdmDatabaseSchema` to own the `SyntaxObject`.

      Returns:
      A `SyntaxObject`.

    <!-- -->

    - #### fromSyntax

          public static SyntaxObject fromSyntax(java.lang.String syntax,
                                                MdmMetadataProvider metadataProvider,
                                                java.lang.String owner,
                                                boolean isForQuery)

      Creates a `SyntaxObject` from a string in expression syntax, provides an owner for the `SyntaxObject`, and indicates whether the `SyntaxObject` is a `Query`.
      Parameters:
      `syntax` - A `String` that contains the expression that specifies a `SyntaxObject`.

      `metadataProvider` - The `MdmMetadataProvider` for the current session.

      `owner` - A `String` that is the name of the `MdmDatabaseSchema` to own the `SyntaxObject`.

      `isForQuery` - A `boolean` that indicates whether the expression describes a `Query`.

      Returns:
      A `SyntaxObject`.

    <!-- -->

    - #### fromSyntax

          public static SyntaxObject fromSyntax(java.lang.String syntax,
                                                MdmMetadataProvider metadataProvider,
                                                java.lang.String owner,
                                                boolean isForQuery,
                                                java.util.List<Query> queries)
                                         throws SyntaxException

      Creates a `SyntaxObject` from a string in expression syntax, provides an owner for the `SyntaxObject`, indicates whether the `SyntaxObject` is a `Query`, and provides the `Query` objects that are referenced by the expression.
      Parameters:
      `syntax` - A `String` that contains the expression that specifies a `SyntaxObject`.

      `metadataProvider` - The `MdmMetadataProvider` for the current session.

      `owner` - A `String` that is the name of the `MdmDatabaseSchema` to own the `SyntaxObject`.

      `isForQuery` - A `boolean` that indicates whether the expression describes a `Query`.

      `queries` - A `List` of `Query` objects that are referenced by the expression.

      Returns:
      A `SyntaxObject`.

      Throws:
      [`SyntaxException`](SyntaxException.md)

    <!-- -->

    - #### fromSyntax

          public static SyntaxObject fromSyntax(java.lang.String syntax,
                                                MdmMetadataProvider metadataProvider,
                                                java.lang.String owner,
                                                boolean isForQuery,
                                                java.util.List<Query> queries,
                                                XMLParserCallback errorCallback)
                                         throws SyntaxException

      Creates a `SyntaxObject` from a string in expression syntax supplied by a `Reader`, provides an owner for the `SyntaxObject`, indicates whether the `SyntaxObject` is a `Query`, provides the `Query` objects that are referenced by the expression, and provides an `XMLParserCallback`.
      Parameters:
      `syntax` - A `String` that contains the expression that specifies a `SyntaxObject`.

      `metadataProvider` - The `MdmMetadataProvider` for the current session.

      `owner` - A `String` that is the name of the `MdmDatabaseSchema` to own the `SyntaxObject`.

      `isForQuery` - A `boolean` that indicates whether the expression describes a `Query`.

      `queries` - A `List` of `Query` objects that are referenced by the expression.

      `errorCallback` - A `XMLParserCallback` that an application can use to process invalid object identifiers.

      Returns:
      A `SyntaxObject`.

      Throws:
      [`SyntaxException`](SyntaxException.md)

    <!-- -->

    - #### isValid

          public final boolean isValid()

      Indicates whether the `SyntaxObject` has any `UnresolvedMetadataObjectReference` objects associated with it.
      Returns:
      A `boolean` that is `true` if the `SyntaxObject` does not have any `UnresolvedMetadataObjectReference` objects or `false` if it does.

    <!-- -->

    - #### equals

          public final boolean equals(SyntaxObject synObject,
                                      boolean bIgnorecase)

      Compares the string representation of the specified `SyntaxObject` with that of this `SyntaxObject`.
      Parameters:
      `synObject` - The `SyntaxObject` to compare with this one.

      `bIgnorecase` - A `boolean` that indicates whether or not to ignore case in the comparison. Specify `true` to ignore case differences or `false` to consider case.

      Returns:
      A `boolean` that is `true` if the string representations are the same or `false` if they are not the same.

    <!-- -->

    - #### equals

          public final boolean equals(SyntaxObject synObject)

      Performs a case-sensitive comparison between the string representation of the specified `SyntaxObject` and that of this `SyntaxObject`.
      Parameters:
      `synObject` - The `SyntaxObject` to compare with this one.

      Returns:
      A `boolean` that is `true` if the string representations are the same or `false` if they are not the same.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](SyntaxException.md)
- [Next Class](SyntaxObjectVisitor.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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
