Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](PathNotFoundException.md)**
- **[Next Class](PropertyIterator.md)**

<!-- -->

- **[Frames](../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**javax.jcr**

## **Interface Property**

- **All Superinterfaces:**
  **[Item](Item.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface Property
      extends Item

  **A `Property` object represents the smallest granularity of content storage. A property must have one and only one parent node. A property does not have children. When we say that node A "has" property B it means that B is a child of A.**
  **A property consists of a name and a value. See [`Value`](Value.md).**

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                      | Method and Description                                                                                                                                                                                                                                |
    |--------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                              | `getBoolean``()`<br>Returns a `boolean` representation of the value of this property.                                                                                                                                                                 |
    | `java.util.Calendar`                                   | `getDate``()`<br>Returns a `Calendar` representation of the value of this property.                                                                                                                                                                   |
    | [`PropertyDefinition`](nodetype/PropertyDefinition.md) | `getDefinition``()`<br>Returns the property definition that applies to this property.                                                                                                                                                                 |
    | `double`                                               | `getDouble``()`<br>Returns a `double` representation of the value of this property.                                                                                                                                                                   |
    | `long`                                                 | `getLength``()`<br>Returns the length of the value of this property.                                                                                                                                                                                  |
    | `long[]`                                               | `getLengths``()`<br>Returns an array holding the lengths of the values of this (multi-value) property in bytes if the values are `PropertyType.BINARY`, otherwise it returns the number of characters needed to display the value in its string form. |
    | `long`                                                 | `getLong``()`<br>Returns a `long` representation of the value of this property.                                                                                                                                                                       |
    | [`Node`](Node.md)                                      | `getNode``()`<br>If this property is of type `REFERENCE` this method returns the node to which this property refers.                                                                                                                                  |
    | `java.io.InputStream`                                  | `getStream``()`<br>Returns an `InputStream` representation of the value of this property.                                                                                                                                                             |
    | `java.lang.String`                                     | `getString``()`<br>Returns a `String` representation of the value of this property.                                                                                                                                                                   |
    | `int`                                                  | `getType``()`<br>Returns the type of this `Property`.                                                                                                                                                                                                 |
    | [`Value`](Value.md)                                    | `getValue``()`<br>Returns the value of this property as a generic `Value` object.                                                                                                                                                                     |
    | [`Value`](Value.md)`[]`                                | `getValues``()`<br>Returns an array of all the values of this property.                                                                                                                                                                               |
    | `void`                                                 | `setValue``(boolean value)`<br>Sets the value of this property to `value`.                                                                                                                                                                            |
    | `void`                                                 | `setValue``(java.util.Calendar value)`<br>Sets the value of this property to `value`.                                                                                                                                                                 |
    | `void`                                                 | `setValue``(double value)`<br>Sets the value of this property to `value`.                                                                                                                                                                             |
    | `void`                                                 | `setValue``(java.io.InputStream value)`<br>Sets the value of this property to `value`.                                                                                                                                                                |
    | `void`                                                 | `setValue``(long value)`<br>Sets the value of this property to `value`.                                                                                                                                                                               |
    | `void`                                                 | `setValue``(`[`Node`](Node.md)` value)`<br>Sets this REFERENCE property to refer to the specified node.                                                                                                                                               |
    | `void`                                                 | `setValue``(java.lang.String value)`<br>Sets the value of this property to `value`.                                                                                                                                                                   |
    | `void`                                                 | `setValue``(java.lang.String[] values)`<br>Sets the value of this property to the `values` array.                                                                                                                                                     |
    | `void`                                                 | `setValue``(`[`Value`](Value.md)` value)`<br>Sets the value of this property to `value`.                                                                                                                                                              |
    | `void`                                                 | `setValue``(`[`Value`](Value.md)`[] values)`<br>Sets the value of this property to the `values` array.                                                                                                                                                |

    - ### Methods inherited from interface javax.jcr.[Item](Item.md)

      [`accept`](Item.md)`, `[`getAncestor`](Item.md)`, `[`getDepth`](Item.md)`, `[`getName`](Item.md)`, `[`getParent`](Item.md)`, `[`getPath`](Item.md)`, `[`getSession`](Item.md)`, `[`isModified`](Item.md)`, `[`isNew`](Item.md)`, `[`isNode`](Item.md)`, `[`isSame`](Item.md)`, `[`refresh`](Item.md)`, `[`remove`](Item.md)`, `[`save`](Item.md)

<!-- -->

- - ### Method Detail

    - #### setValue

          void setValue(Value value)
                 throws ValueFormatException,
                        VersionException,
                        LockException,
                        ConstraintViolationException,
                        RepositoryException

      Sets the value of this property to `value`. If this property's property type is not constrained by the node type of its parent node, then the property type is changed to that of the supplied `value`. If the property type is constrained, then a best-effort conversion is attempted. If conversion fails, a `ValueFormatException` is thrown immediately (not on `save`). The change will be persisted (if valid) on `save`
      A `ConstraintViolationException` will be thrown either immediately or on `save`, if the change would violate a node type or implementation-specific constraint. Implementations may differ on when this validation is performed.

      A `VersionException` will be thrown either immediately or on `save`, if this property belongs to a node that is versionable and checked-in or is non-versionable but whose nearest versionable ancestor is checked-in. Implementations may differ on when this validation is performed.

      A `LockException` will be thrown either immediately or on `save`, if a lock prevents the setting of the value. Implementations may differ on when this validation is performed.

      Parameters:
      `value` - The new value to set the property to.

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if the type or format of the specified value is incompatible with the type of this property.

      [`VersionException`](version/VersionException.md) - if this property belongs to a node that is versionable and checked-in or is non-versionable but whose nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`.

      [`LockException`](lock/LockException.md) - if a lock prevents the setting of the value and this implementation performs this validation immediately instead of waiting until `save`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if the change would violate a node-type or other constraint and this implementation performs this validation immediately instead of waiting until `save`.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### setValue

          void setValue(Value[] values)
                 throws ValueFormatException,
                        VersionException,
                        LockException,
                        ConstraintViolationException,
                        RepositoryException

      Sets the value of this property to the `values` array. If this property's property type is not constrained by the node type of its parent node, then the property type is changed to that of the supplied `values`. If the property type is constrained, then a best-effort conversion is attempted. If conversion fails, a `ValueFormatException` is thrown immediately (not on `save`). If this property is not a multi-valued then a `ValueFormatException` is thrown immediately. The change will be persisted (if valid) on `save`.
      A `ConstraintViolationException` will be thrown either immediately or on `save`, if the change would violate a node type or implementation-specific constraint. Implementations may differ on when this validation is performed.

      A `VersionException` will be thrown either immediately or on `save`, if this property belongs to a node that is versionable and checked-in or is non-versionable but whose nearest versionable ancestor is checked-in. Implementations may differ on when this validation is performed.

      A `LockException` will be thrown either immediately or on `save`, if a lock prevents the setting of the value. Implementations may differ on when this validation is performed.

      Parameters:
      `values` - The new values to set the property to.

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if the type or format of the specified values is incompatible with the type of this property.

      [`VersionException`](version/VersionException.md) - if this property belongs to a node that is versionable and checked-in or is non-versionable but whose nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`.

      [`LockException`](lock/LockException.md) - if a lock prevents the setting of the value and this implementation performs this validation immediately instead of waiting until `save`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if the change would violate a node-type or other constraint and this implementation performs this validation immediately instead of waiting until `save`.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### setValue

          void setValue(java.lang.String value)
                 throws ValueFormatException,
                        VersionException,
                        LockException,
                        ConstraintViolationException,
                        RepositoryException

      Sets the value of this property to `value`. Same as `setValue(Value value)` except that the value is specified as a `String`.
      Parameters:
      `value` - The new value to set the property to.

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if the type or format of the specified value is incompatible with the type of this property.

      [`VersionException`](version/VersionException.md) - if this property belongs to a node that is versionable and checked-in or is non-versionable but whose nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`.

      [`LockException`](lock/LockException.md) - if a lock prevents the setting of the value and this implementation performs this validation immediately instead of waiting until `save`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if the change would violate a node-type or other constraint and this implementation performs this validation immediately instead of waiting until `save`.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### setValue

          void setValue(java.lang.String[] values)
                 throws ValueFormatException,
                        VersionException,
                        LockException,
                        ConstraintViolationException,
                        RepositoryException

      Sets the value of this property to the `values` array. Same as `setValue(Value[] values)` except that the values are specified as a `String[]`.
      Parameters:
      `values` - The new values to set the property to.

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if the type or format of the specified values is incompatible with the type of this property.

      [`VersionException`](version/VersionException.md) - if this property belongs to a node that is versionable and checked-in or is non-versionable but whose nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`.

      [`LockException`](lock/LockException.md) - if a lock prevents the setting of the value and this implementation performs this validation immediately instead of waiting until `save`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if the change would violate a node-type or other constraint and this implementation performs this validation immediately instead of waiting until `save`.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### setValue

          void setValue(java.io.InputStream value)
                 throws ValueFormatException,
                        VersionException,
                        LockException,
                        ConstraintViolationException,
                        RepositoryException

      Sets the value of this property to `value`. Same as `setValue(Value value)` except that the value is specified as a `InputStream`.
      Parameters:
      `value` - The new value to set the property to.

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if the type or format of the specified value is incompatible with the type of this property.

      [`VersionException`](version/VersionException.md) - if this property belongs to a node that is versionable and checked-in or is non-versionable but whose nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`.

      [`LockException`](lock/LockException.md) - if a lock prevents the setting of the value and this implementation performs this validation immediately instead of waiting until `save`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if the change would violate a node-type or other constraint and this implementation performs this validation immediately instead of waiting until `save`.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### setValue

          void setValue(long value)
                 throws ValueFormatException,
                        VersionException,
                        LockException,
                        ConstraintViolationException,
                        RepositoryException

      Sets the value of this property to `value`. Same as `setValue(Value value)` except that the value is specified as a `long`.
      Parameters:
      `value` - The new value to set the property to.

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if the type or format of the specified value is incompatible with the type of this property.

      [`VersionException`](version/VersionException.md) - if this property belongs to a node that is versionable and checked-in or is non-versionable but whose nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`.

      [`LockException`](lock/LockException.md) - if a lock prevents the setting of the value and this implementation performs this validation immediately instead of waiting until `save`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if the change would violate a node-type or other constraint and this implementation performs this validation immediately instead of waiting until `save`.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### setValue

          void setValue(double value)
                 throws ValueFormatException,
                        VersionException,
                        LockException,
                        ConstraintViolationException,
                        RepositoryException

      Sets the value of this property to `value`. Same as `setValue(Value value)` except that the value is specified as a `double`.
      Parameters:
      `value` - The new value to set the property to.

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if the type or format of the specified value is incompatible with the type of this property.

      [`VersionException`](version/VersionException.md) - if this property belongs to a node that is versionable and checked-in or is non-versionable but whose nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`.

      [`LockException`](lock/LockException.md) - if a lock prevents the setting of the value and this implementation performs this validation immediately instead of waiting until `save`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if the change would violate a node-type or other constraint and this implementation performs this validation immediately instead of waiting until `save`.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### setValue

          void setValue(java.util.Calendar value)
                 throws ValueFormatException,
                        VersionException,
                        LockException,
                        ConstraintViolationException,
                        RepositoryException

      Sets the value of this property to `value`. Same as `setValue(Value value)` except that the value is specified as a `Calendar`.
      Parameters:
      `value` - The new value to set the property to.

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if the type or format of the specified value is incompatible with the type of this property.

      [`VersionException`](version/VersionException.md) - if this property belongs to a node that is versionable and checked-in or is non-versionable but whose nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`.

      [`LockException`](lock/LockException.md) - if a lock prevents the setting of the value and this implementation performs this validation immediately instead of waiting until `save`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if the change would violate a node-type or other constraint and this implementation performs this validation immediately instead of waiting until `save`.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### setValue

          void setValue(boolean value)
                 throws ValueFormatException,
                        VersionException,
                        LockException,
                        ConstraintViolationException,
                        RepositoryException

      Sets the value of this property to `value`. Same as `setValue(Value value)` except that the value is specified as a `boolean`.
      Parameters:
      `value` - The new value to set the property to.

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if the type or format of the specified value is incompatible with the type of this property.

      [`VersionException`](version/VersionException.md) - if this property belongs to a node that is versionable and checked-in or is non-versionable but whose nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`.

      [`LockException`](lock/LockException.md) - if a lock prevents the setting of the value and this implementation performs this validation immediately instead of waiting until `save`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if the change would violate a node-type or other constraint and this implementation performs this validation immediately instead of waiting until `save`.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### setValue

          void setValue(Node value)
                 throws ValueFormatException,
                        VersionException,
                        LockException,
                        ConstraintViolationException,
                        RepositoryException

      Sets this REFERENCE property to refer to the specified node. If this property is not of type REFERENCE or the specified node is not referenceable (i.e., is not of mixin node type `mix:referenceable` and therefore does not have a UUID) then a `ValueFormatException` is thrown.
      Parameters:
      `value` - The node to which this REFERENCE property will refer.

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if the type or format of the specified value is incompatible with the type of this property.

      [`VersionException`](version/VersionException.md) - if this property belongs to a node that is versionable and checked-in or is non-versionable but whose nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`.

      [`LockException`](lock/LockException.md) - if a lock prevents the setting of the value and this implementation performs this validation immediately instead of waiting until `save`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if the change would violate a node-type or other constraint and this implementation performs this validation immediately instead of waiting until `save`.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### getValue

          Value getValue()
                  throws ValueFormatException,
                         RepositoryException

      Returns the value of this property as a generic `Value` object.
      If the property is multi-valued, this method throws a `ValueFormatException`.

      The object returned is a copy of the stored value and is immutable.

      Returns:
      the value

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if the property is multi-valued.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### getValues

          Value[] getValues()
                     throws ValueFormatException,
                            RepositoryException

      Returns an array of all the values of this property. Used to access multi-value properties. If the property is single-valued, this method throws a `ValueFormatException`. The array returned is a copy of the stored values, so changes to it are not reflected in internal storage.
      Returns:
      a `Value` array

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if the property is single-valued.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### getString

          java.lang.String getString()
                              throws ValueFormatException,
                                     RepositoryException

      Returns a `String` representation of the value of this property. A shortcut for `Property.getValue().getString()`. See [`Value`](Value.md). If this property is multi-valued, this method throws a `ValueFormatException`.
      If the value of this property cannot be converted to a string, a `ValueFormatException` is thrown.

      A `RepositoryException` is thrown if another error occurs.

      Returns:
      A string representation of the value of this property.

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if conversion to a string is not possible or if the property is multi-valued.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### getStream

          java.io.InputStream getStream()
                                 throws ValueFormatException,
                                        RepositoryException

      Returns an `InputStream` representation of the value of this property. A shortcut for `Property.getValue().getStream()`. See [`Value`](Value.md).
      If this property is multi-valued, this method throws a `ValueFormatException`.

      A `RepositoryException` is thrown if another error occurs.

      Returns:
      A stream representation of the value of this property.

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if the property is multi-valued.

      [`RepositoryException`](RepositoryException.md) - if another error occurs

    <!-- -->

    - #### getLong

          long getLong()
                throws ValueFormatException,
                       RepositoryException

      Returns a `long` representation of the value of this property. A shortcut for `Property.getValue().getLong()`. See [`Value`](Value.md). If this property is multi-valued, this method throws a `ValueFormatException`.
      If the value of this property cannot be converted to a `long`, a `ValueFormatException` is thrown.

      A `RepositoryException` is thrown if another error occurs.

      Returns:
      A `long` representation of the value of this property.

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if conversion to a string is not possible or if the property is multi-valued.

      [`RepositoryException`](RepositoryException.md) - if another error occurs

    <!-- -->

    - #### getDouble

          double getDouble()
                    throws ValueFormatException,
                           RepositoryException

      Returns a `double` representation of the value of this property. A shortcut for `Property.getValue().getDouble()`. See [`Value`](Value.md). If this property is multi-valued, this method throws a `ValueFormatException`.
      If the value of this property cannot be converted to a double, a `ValueFormatException` is thrown.

      A `RepositoryException` is thrown if another error occurs.

      Returns:
      A double representation of the value of this property.

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if conversion to a string is not possible or if the property is multi-valued.

      [`RepositoryException`](RepositoryException.md) - if another error occurs

    <!-- -->

    - #### getDate

          java.util.Calendar getDate()
                              throws ValueFormatException,
                                     RepositoryException

      Returns a `Calendar` representation of the value of this property. A shortcut for `Property.getValue().getDate()`. See [`Value`](Value.md).
      The object returned is a copy of the stored value, so changes to it are not reflected in internal storage.

      If this property is multi-valued, this method throws a `ValueFormatException`.

      If the value of this property cannot be converted to a date, a `ValueFormatException` is thrown.

      A `RepositoryException` is thrown if another error occurs.

      Returns:
      A date (`Calendar` object) representation of the value of this property.

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if conversion to a string is not possible or if the property is multi-valued.

      [`RepositoryException`](RepositoryException.md) - if another error occurs

    <!-- -->

    - #### getBoolean

          boolean getBoolean()
                      throws ValueFormatException,
                             RepositoryException

      Returns a `boolean` representation of the value of this property. A shortcut for `Property.getValue().getBoolean()`. See [`Value`](Value.md). If this property is multi-valued, this method throws a `ValueFormatException`.
      If the value of this property cannot be converted to a boolean, a `ValueFormatException` is thrown.

      A `RepositoryException` is thrown if another error occurs.

      Returns:
      A boolean representation of the value of this property.

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if conversion to a string is not possible or if the property is multi-valued.

      [`RepositoryException`](RepositoryException.md) - if another error occurs

    <!-- -->

    - #### getNode

          Node getNode()
                throws ValueFormatException,
                       RepositoryException

      If this property is of type `REFERENCE` this method returns the node to which this property refers.
      If this property is multi-valued, this method throws a `ValueFormatException`.

      If this property cannot be coverted to a reference, then a `ValueFormatException` is thrown.

      If this property is a REFERENCE property but is currently part of the frozen state of a version in version storage, this method will throw a `ValueFormatException`.

      A `RepositoryException` is thrown if another error occurs.

      Returns:
      the referenced Node

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if this property cannot be converted to a reference, if the property is multi-valued or if this property is a REFERENCE property but is currently part of the frozen state of a version in version storage.

      [`RepositoryException`](RepositoryException.md) - if another error occurs

    <!-- -->

    - #### getLength

          long getLength()
                  throws ValueFormatException,
                         RepositoryException

      Returns the length of the value of this property.
      Returns the length in bytes if the value is a `PropertyType.BINARY`, otherwise it returns the number of characters needed to display the value in its string form.

      Returns -1 if the implementation cannot determine the length.

      If this property is multi-valued, this method throws a `ValueFormatException`.

      Returns:
      an `long`.

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if this property is multi-valued.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### getLengths

          long[] getLengths()
                     throws ValueFormatException,
                            RepositoryException

      Returns an array holding the lengths of the values of this (multi-value) property in bytes if the values are `PropertyType.BINARY`, otherwise it returns the number of characters needed to display the value in its string form. The order of the length values corresponds to the order of the values in the property.
      Returns a `-1` in the appropriate position if the implementation cannot determine the length of a value.

      If this property is single-valued, this method throws a `ValueFormatException`.

      A RepositoryException is thrown if another error occurs.

      Returns:
      an array of lengths

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if this property is single-valued.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### getDefinition

          PropertyDefinition getDefinition()
                                    throws RepositoryException

      Returns the property definition that applies to this property. In some cases there may appear to be more than one definition that could apply to this node. However, it is assumed that upon creation of this property, a single particular definition was used and it is *that* definition that this method returns. How this governing definition is selected upon property creation from among others which may have been applicable is an implementation issue and is not covered by this specification.
      Returns:
      a `PropertyDefinition` object.

      Throws:
      [`RepositoryException`](RepositoryException.md) - if an error occurs.

      See Also:
      [`NodeType.getPropertyDefinitions()`](nodetype/NodeType.md)

    <!-- -->

    - #### getType

          int getType()
               throws RepositoryException

      Returns the type of this `Property`. One of:
      - `PropertyType.STRING`
      - `PropertyType.BINARY`
      - `PropertyType.DATE`
      - `PropertyType.DOUBLE`
      - `PropertyType.LONG`
      - `PropertyType.BOOLEAN`
      - `PropertyType.NAME`
      - `PropertyType.PATH`
      - `PropertyType.REFERENCE`

      The type returned is that which was set at property creation. Note that for some property `p`, the type returned by `p.getType()` may differ from the type returned by `p.getDefinition.getRequiredType()` only in the case where the latter returns `UNDEFINED`. The type of a property instance is never `UNDEFINED` (it must always have some actual type).
      Returns:
      an int

      Throws:
      [`RepositoryException`](RepositoryException.md) - if an error occurs

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](PathNotFoundException.md)**
- **[Next Class](PropertyIterator.md)**

<!-- -->

- **[Frames](../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**Copyright © 2004-2005 Day Software Management AG. All Rights Reserved.**
