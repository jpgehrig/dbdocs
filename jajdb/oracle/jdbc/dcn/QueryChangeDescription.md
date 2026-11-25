Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/QueryChangeDescription.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](DatabaseChangeRegistration.md)
- [Next Class](QueryChangeDescription.QueryChangeEventType.md)

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

oracle.jdbc.dcn

## Interface QueryChangeDescription

-

  ------------------------------------------------------------------------



      public interface QueryChangeDescription

  This interface describes a query result change.
  The information includes:

  - The query id;
  - The type of query change event;
  - A description at the table level of the changes that affect the result of the query..

  Since:
  11.1

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Interface and Description                                                                        |
    |-------------------|--------------------------------------------------------------------------------------------------|
    | `static class `   | [`QueryChangeDescription.QueryChangeEventType`](QueryChangeDescription.QueryChangeEventType.md)  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                               | Method and Description                                                                              |
    |-------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
    | [`QueryChangeDescription.QueryChangeEventType`](QueryChangeDescription.QueryChangeEventType.md) | `getQueryChangeEventType``()`<br>Returns the type of query change event.                            |
    | `long`                                                                                          | `getQueryId``()`<br>Returns the id of the query which result has changed.                           |
    | [`TableChangeDescription`](TableChangeDescription.md)`[]`                                       | `getTableChangeDescription``()`<br>Returns the table level change description of this query result. |

<!-- -->

- - ### Method Detail

    - #### getQueryId

          long getQueryId()

      Returns the id of the query which result has changed.

    <!-- -->

    - #### getQueryChangeEventType

          QueryChangeDescription.QueryChangeEventType getQueryChangeEventType()

      Returns the type of query change event.

    <!-- -->

    - #### getTableChangeDescription

          TableChangeDescription[] getTableChangeDescription()

      Returns the table level change description of this query result.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/QueryChangeDescription.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](DatabaseChangeRegistration.md)
- [Next Class](QueryChangeDescription.QueryChangeEventType.md)

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

Copyright © 2008, 2022, Oracle and/or its affiliates.
