Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](NoSuchNodeTypeException.md)**
- **Next Class**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

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

**javax.jcr.nodetype**

## **Interface PropertyDefinition**

- **All Superinterfaces:**
  **[ItemDefinition](ItemDefinition.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface PropertyDefinition
      extends ItemDefinition

  **A property definition. Used in node type definitions.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type          | Method and Description                                                      |
    |----------------------------|-----------------------------------------------------------------------------|
    | [`Value`](../Value.md)`[]` | `getDefaultValues``()`<br>Gets the default value(s) of the property.        |
    | `int`                      | `getRequiredType``()`<br>Gets the required type of the property.            |
    | `java.lang.String[]`       | `getValueConstraints``()`<br>Gets the array of constraint strings.          |
    | `boolean`                  | `isMultiple``()`<br>Reports whether this property can have multiple values. |

    - ### Methods inherited from interface javax.jcr.nodetype.[ItemDefinition](ItemDefinition.md)

      [`getDeclaringNodeType`](ItemDefinition.md)`, `[`getName`](ItemDefinition.md)`, `[`getOnParentVersion`](ItemDefinition.md)`, `[`isAutoCreated`](ItemDefinition.md)`, `[`isMandatory`](ItemDefinition.md)`, `[`isProtected`](ItemDefinition.md)

<!-- -->

- - ### Method Detail

    - #### getRequiredType

          int getRequiredType()

      Gets the required type of the property. One of:
      - `PropertyType.STRING`
      - `PropertyType.DATE`
      - `PropertyType.BINARY`
      - `PropertyType.DOUBLE`
      - `PropertyType.LONG`
      - `PropertyType.BOOLEAN`
      - `PropertyType.NAME`
      - `PropertyType.PATH`
      - `PropertyType.REFERENCE`
      - `PropertyType.UNDEFINED`

      `PropertyType.UNDEFINED` is returned if this property may be of any type.
      Returns:
      an int

    <!-- -->

    - #### getValueConstraints

          java.lang.String[] getValueConstraints()

      Gets the array of constraint strings. Each string in the array specifies a constraint on the value of the property. The constraints are OR-ed together, meaning that in order to be valid, the value must meet at least one of the constraints. For example, a constraint array of `["constraint1", "constraint2", "constraint3"]` has the interpretation: "the value of this property must meet either constraint1, constraint2 or constraint3".
      Reporting of value constraints is optional. An implementation may return `null`, indicating that value constraint information is unavailable (though a constraint may still exist).

      Returning an empty array, on the other hand, indicates that value constraint information is available and that no constraints are placed on this value.

      In the case of multi-value properties, the constraint string array returned applies to all the values of the property.

      The constraint strings themselves having differing formats and interpretations depending on the type of the property in question. The following describes the value constraint syntax for each property type:

      - `STRING`: The constraint string is a regular expression pattern. For example the regular expression "`.*`" means "any string, including the empty string". Whereas a simple literal string (without any RE-specific meta-characters) like "`banana`" matches only the string "`banana`".
      - `PATH`: The constraint string is a *JCR path* with an optional "`*`" character after the last "`/`" character. For example, possible constraint strings for a property of type `PATH` include:
        1.  "`/myapp:products/myapp:televisions`"
        2.  "`/myapp:products/myapp:televisions/`"
        3.  "`/myapp:products/*`"
        4.  "`myapp:products/myapp:televisions`"
        5.  "`../myapp:televisions`"
        6.  "`../myapp:televisions/*`"

        The following principles apply:
        - The "\*" means "matches descendants" not "matches any subsequent path". For example, `/a/*` does not match `/a/../c`. The constraint must match the normalized path.
        - Relative path constraint only match relative path values and absolute path constraints only match absolute path values.
        - A trailing "`/`" has no effect (hence, `1` and `2`, above, are equivalent).
        - The trailing "`*`" character means that the value of the `PATH` property is restricted to the indicated subtree (in other words any additional relative path can replace the "`*`"). For example, 3, above would allow `/myapp:products/myapp:radios`, `/myapp:products/myapp:microwaves/X900`, and so forth.
        - A constraint without a "`*`" means that the `PATH` property is restricted to that precise path. For example, `1`, above, would allow only the value `/myapp:products/myapp:televisions`.
        - The constraint can indicate either a relative path or an absolute path depending on whether it includes a leading "`/`" character. `1` and `4`, above for example, are distinct.
        - The string returned must reflect the namespace mapping in the current `Session` (i.e., the current state of the namespace registry overlaid with any session-specific mappings). Constraint strings for `PATH` properties should be stored in fully-qualified form (using the actual URI instead of the prefix) and then be converted to prefix form according to the current mapping upon the `PropertyDefinition.getValueConstraints` call.
      - `NAME`: The constraint string is a *JCR name* in prefix form. For example "`myapp:products`". No wildcards or other pattern matching are supported. As with `PATH` properties, the string returned must reflect the namespace mapping in the current `Session`. Constraint strings for `NAME` properties should be stored in fully-qualified form (using the actual URI instead of the prefix) and then be converted to prefix form according to the current mapping.
      - `REFERENCE`: The constraint string is a *JCR name* in prefix form. This name is interpreted as a node type name and the `REFERENCE` property is restricted to referring only to nodes that have at least the indicated node type. For example, a constraint of "`mytype:document`" would indicate that the REFERENCE property in question can only refer to nodes that have at least the node type `mytype:document` (assuming this was the only constraint returned in the array, recall that the array of constraints are to be "OR-ed" together). No wildcards or other pattern matching are supported. As with `PATH` properties, the string returned must reflect the namespace mapping in the current `Session`. Constraint strings for `REFERENCE` properties should be stored in fully-qualified form (using the actual URI instead of the prefix) and then be converted to prefix form according to the current mapping.
      - `BOOLEAN`: Either "`true`" or "`false`".

      The remaining types all have value constraints in the form of inclusive or exclusive ranges: i.e., "`[min, max]`", "`(min, max)`", "`(min, max]`" or "`[min, max)`". Where "`[`" and "`]`" indicate "inclusive", while "`(`" and "`)`" indicate "exclusive". A missing `min` or `max` value indicates no bound in that direction. For example \[,5\] means no minimum but a maximum of 5 (inclusive) while \[,\] means simply that any value will suffice, The meaning of the `min` and `max` values themselves differ between types as follows:
      - `BINARY`: `min` and `max` specify the allowed size range of the binary value in bytes.
      - `DATE`: `min` and `max` are dates specifying the allowed date range. The date strings must be in the ISO8601-compliant format: `YYYY-MM-DDThh:mm:ss.sssTZD`.
      - `LONG`, `DOUBLE`: min and max are numbers.

      Because constraints are returned as an array of disjunctive constraints, in many cases the elements of the array can serve directly as a "choice list". This may, for example, be used by an application to display options to the end user indicating the set of permitted values.
      Returns:
      a `String` array.

    <!-- -->

    - #### getDefaultValues

          Value[] getDefaultValues()

      Gets the default value(s) of the property. These are the values that the property defined by this PropertyDefinition will be assigned if it is automatically created (that is, if [`ItemDefinition.isAutoCreated()`](ItemDefinition.md) returns `true`).
      This method returns an array of Value objects. If the property is multi-valued, then this array represents the full set of values that the property will be assigned upon being auto-created. Note that this could be the empty array. If the property is single-valued, then the array returned will be of size 1.

      If `null` is returned, then the property has no fixed default value. This does not exclude the possibility that the property still assumes some value automatically, but that value may be parameterized (for example, "the current date") and hence not expressable as a single fixed value. In particular, this *must* be the case if `isAutoCreated` returns `true` and this method returns `null`.

      Returns:
      an array of `Value` objects.

    <!-- -->

    - #### isMultiple

          boolean isMultiple()

      Reports whether this property can have multiple values. Note that the `isMultiple` flag is special in that a given node type may have two property definitions that are identical in every respect except for the their `isMultiple` status. For example, a node type can specify two string properties both called `X`, one of which is multi-valued and the other not.
      Returns:
      a `boolean`

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](NoSuchNodeTypeException.md)**
- **Next Class**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

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
