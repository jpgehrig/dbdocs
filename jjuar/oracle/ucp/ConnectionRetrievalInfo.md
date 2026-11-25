Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ConnectionRetrievalInfo.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](ConnectionLabelingCallback.md)
- [Next Class](NoAvailableConnectionsException.md)

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

oracle.ucp

## Interface ConnectionRetrievalInfo

-

  ------------------------------------------------------------------------



      public interface ConnectionRetrievalInfo

  The connection retrieval info object is used by the connection factory adapter to create connections. It contains resource-specific information that the connection factory adapter uses to create connections. For example, the JDBC connection retrieval info object maintains the user and password that are used to create a connection from a JDBC resource.
  The connection retrieval info object also provides methods for equality and hash so that like-connections can be pooled efficiently.

  The connection retrieval object supports Connection Labeling, a common mechanism for all types of connections. Represented as key/value pairs, connection labels are used for application-driven connection matching purposes.

  See Also:
  [`ConnectionFactoryAdapter`](ConnectionFactoryAdapter.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type         | Method and Description                                                                                                               |
    |---------------------------|--------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                    | `addLabel``(java.lang.String key, java.lang.String value)`<br>Adds a connection label to this connection retrieval info object.      |
    | `boolean`                 | `equals``(java.lang.Object other)`<br>Checks whether this instance is equal to another.                                              |
    | `boolean`                 | `equalsIncludingPassword``(ConnectionRetrievalInfo cri)`<br>Checks whether this instance is equal to another.                        |
    | `ConnectionRetrievalInfo` | `getCopyWithNoLabels``()`<br>Clones this connection retrieval object but removes all the connection labels associated.               |
    | `java.util.Properties`    | `getLabels``()`<br>Retrieves all the connection labels stored on this connection retrieval info object.                              |
    | `int`                     | `hashCode``()`<br>Returns the `hashCode` of the `ConnectionRequestInfo.`                                                             |
    | `void`                    | `removeLabel``(java.lang.String key)`<br>Removes the connection label with the given key from this connection retrieval info object. |

<!-- -->

- - ### Method Detail

    - #### equals

          boolean equals(java.lang.Object other)

      Checks whether this instance is equal to another. This method must be implemented since `ConnectionRetrievalInfo` is defined specific to the type of object being pooled. The conditions for equality are specific to the type of object being pooled.
      Overrides:
      `equals` in class `java.lang.Object`

      Returns:
      `true` if the two instances are equal; `false` otherwise.

    <!-- -->

    - #### hashCode

          int hashCode()

      Returns the `hashCode` of the `ConnectionRequestInfo.`
      Overrides:
      `hashCode` in class `java.lang.Object`

      Returns:
      The hash code of this instance.

    <!-- -->

    - #### addLabel

          void addLabel(java.lang.String key,
                        java.lang.String value)
                 throws UniversalConnectionPoolException

      Adds a connection label to this connection retrieval info object. This can be used for both requested labels during a connection borrowing request or actual labels applied on a borrowed connection. The addition of connection labels is cumulative; the supplied key/value pair is added to those connection labels already on this object each time this method is called. However, for each particular label key, only the last applied value is retained.
      Parameters:
      `key` - The key of the connection label to be added. Cannot be `null` or an empty string.

      `value` - The value of the connection label to be added. Can be `null` or an empty string.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - If the key is `null` or an empty string.

    <!-- -->

    - #### removeLabel

          void removeLabel(java.lang.String key)
                    throws UniversalConnectionPoolException

      Removes the connection label with the given key from this connection retrieval info object. This method does nothing if there is no label stored on this object with the specified key.
      Parameters:
      `key` - The key of the connection label to be removed. Cannot be `null` or an empty string.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - If the key is `null` or an empty string.

    <!-- -->

    - #### getCopyWithNoLabels

          ConnectionRetrievalInfo getCopyWithNoLabels()

      Clones this connection retrieval object but removes all the connection labels associated.
      Returns:
      A clone `ConnectionRetrievalInfo` object with all connection labels removed.

    <!-- -->

    - #### getLabels

          java.util.Properties getLabels()

      Retrieves all the connection labels stored on this connection retrieval info object. Any change to the result Properties object does not affect the stored labels.
      Returns:
      A `java.util.Properties` object storing all the stored labels as key/value pairs. Returns `null` if there are no stored labels on this connection retrieval info object.

    <!-- -->

    - #### equalsIncludingPassword

          boolean equalsIncludingPassword(ConnectionRetrievalInfo cri)

      Checks whether this instance is equal to another. This method also checks for password equality in addition to the equals method.
      Parameters:
      `cri` - Connection retrieval info object.

      Returns:
      Returns true, if the given CRI is equal to the current instance CRI including password field.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ConnectionRetrievalInfo.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](ConnectionLabelingCallback.md)
- [Next Class](NoAvailableConnectionsException.md)

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

Copyright © 2007, 2022, Oracle and/or its affiliates.
