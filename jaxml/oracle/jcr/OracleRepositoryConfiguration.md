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

- **[Prev Class](OracleRepository.md)**
- **[Next Class](OracleRepositoryFactory.md)**

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

**oracle.jcr**

## **Interface OracleRepositoryConfiguration**

- **All Superinterfaces:**
  **javax.naming.Referenceable, java.io.Serializable**

  <!-- -->

  **All Known Implementing Classes:**
  **[XDBRepositoryConfiguration](xdb/XDBRepositoryConfiguration.md)**

  ------------------------------------------------------------------------

  **Deprecated. **
  **OracleRepositoryConfiguration specifies the configuration of an OracleRepository.**
  **
  **

      public interface OracleRepositoryConfiguration
      extends java.io.Serializable, javax.naming.Referenceable

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type    | Method and Description                                                                                                                                 |
    |----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`   | `getDescriptor``(java.lang.String key)`<br>Deprecated. <br>Gets the value of the specified descriptor key.                                             |
    | `java.lang.String[]` | `getDescriptorKeys``()`<br>Deprecated. <br>Gets the keys of the descriptors contributed to the OracleRepository by this OracleRepositoryConfiguration. |

    - ### Methods inherited from interface javax.naming.Referenceable

      `getReference`

<!-- -->

- - ### Method Detail

    - #### getDescriptorKeys

          java.lang.String[] getDescriptorKeys()

      Deprecated. 
      Gets the keys of the descriptors contributed to the OracleRepository by this OracleRepositoryConfiguration.
      Thd returned keys may be a subset of those returned by OracleRepository `getDescriptorKeys`.

      Returns:
      the keys

    <!-- -->

    - #### getDescriptor

          java.lang.String getDescriptor(java.lang.String key)

      Deprecated. 
      Gets the value of the specified descriptor key.
      Parameters:
      `key` - a key in the set returned by `getDescriptorKeys`

      Returns:
      the value, or null if the key is not found

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

- **[Prev Class](OracleRepository.md)**
- **[Next Class](OracleRepositoryFactory.md)**

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

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
