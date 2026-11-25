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

- **Prev Class**
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

**oracle.jcr.nodetype**

## **Interface OracleNodeTypeManager**

- **All Superinterfaces:**
  **[NodeTypeManager](../../../javax/jcr/nodetype/NodeTypeManager.md)**

  ------------------------------------------------------------------------

  **Deprecated. **
  **OracleNodeTypeManager allows discovery of JCR node types.**
  **For the XML DB Content Connector, OracleNodeTypeManager also allows XML schemas to be registered for use in JCR. Doing so creates JCR node types corresponding to the schema types and global element declarations defined by the XML schema. Schema-based content and metadata will then be exposed as JCR nodes of these node types, instead of the nt:unstructured node type.**

  **Before a schema is registered for use in JCR, it should be registered for use in the database using the `DBMS_XMLSCHEMA.registerschema` PL/SQL procedure. Only globally-registered schemas can be used in JCR.**

  **The list of registered XML schemas is cached by the OracleNodeTypeManager object. The cache is automatically refreshed each time `registerXMLSchema` or `unregisterXMLSchema` is called on the OracleNodeTypeManager object. Call `refresh` to explicitly refresh the cache.**

  **Refer to XDBRepositoryConfiguration for further information on how the list of registered XML schemas is stored by the XML DB Content Connector.**

  **
  **

      public interface OracleNodeTypeManager
      extends NodeTypeManager

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type | Method and Description                                                                                                                                                              |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `refresh``()`<br>Deprecated. <br>Invalidates the in-memory copy of the node type registry and reloads it from the content repository.                                               |
    | `void`            | `registerXMLSchema``(java.lang.String schemaLocation, java.lang.String jcrNodeTypeNamespace)`<br>Deprecated. <br>Registers the XML Schema having the specified schema location URL. |
    | `void`            | `unregisterXMLSchema``(java.lang.String schemaLocation)`<br>Deprecated. <br>Unregisters the XML Schema having the specified schema location URL.                                    |

    - ### Methods inherited from interface javax.jcr.nodetype.[NodeTypeManager](../../../javax/jcr/nodetype/NodeTypeManager.md)

      [`getAllNodeTypes`](../../../javax/jcr/nodetype/NodeTypeManager.md)`, `[`getMixinNodeTypes`](../../../javax/jcr/nodetype/NodeTypeManager.md)`, `[`getNodeType`](../../../javax/jcr/nodetype/NodeTypeManager.md)`, `[`getPrimaryNodeTypes`](../../../javax/jcr/nodetype/NodeTypeManager.md)

<!-- -->

- - ### Method Detail

    - #### refresh

          void refresh()
                throws RepositoryException

      Deprecated. 
      Invalidates the in-memory copy of the node type registry and reloads it from the content repository.
      Throws:
      [`RepositoryException`](../../../javax/jcr/RepositoryException.md) - if the operation fails

    <!-- -->

    - #### registerXMLSchema

          void registerXMLSchema(java.lang.String schemaLocation,
                                 java.lang.String jcrNodeTypeNamespace)
                          throws AccessDeniedException,
                                 RepositoryException

      Deprecated. 
      Registers the XML Schema having the specified schema location URL.
      If the schema is already registered, the JCR node type namespace is updated to the value specified.

      Parameters:
      `schemaLocation` - the schema location; required

      `jcrNodeTypeNamespace` - the namespace into which to create JCR node types, or null to use the target namespace of the schema

      Throws:
      [`AccessDeniedException`](../../../javax/jcr/AccessDeniedException.md) - if the session does not have sufficient privileges to perform the operation

      [`RepositoryException`](../../../javax/jcr/RepositoryException.md) - if the operation otherwise fails

    <!-- -->

    - #### unregisterXMLSchema

          void unregisterXMLSchema(java.lang.String schemaLocation)
                            throws AccessDeniedException,
                                   RepositoryException

      Deprecated. 
      Unregisters the XML Schema having the specified schema location URL.
      Parameters:
      `schemaLocation` - the schema location; required

      Throws:
      [`AccessDeniedException`](../../../javax/jcr/AccessDeniedException.md) - if the session does not have sufficient privileges to perform the operation

      [`RepositoryException`](../../../javax/jcr/RepositoryException.md) - if the operation otherwise fails

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

- **Prev Class**
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

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
