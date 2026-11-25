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

- **Prev Class**
- **[Next Class](OracleNamespaceRegistry.md)**

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

## **Interface CredentialsProvider**

- **All Superinterfaces:**
  **javax.naming.Referenceable, java.io.Serializable**

  ------------------------------------------------------------------------

  **Deprecated. **
  **A CredentialsProvider generates a Credentials object when no Credentials object is supplied to the `login` method of Repository.**
  **JCR allows the Repository `login` method to be called without Credentials (`login()` and `login(String)`) or with null Credentials (`login(Credentials)` and `login(Credentials, String)`).**

  **The Oracle JCR framework allows a CredentialsProvider to be registered with a Repository. The CredentialsProvider method `getCredentials` is called by the JCR framework when no Credentials are supplied to the `login` method. The Credentials returned by this method are used to authenticate and create a JCR session, no differently than if Credentials were supplied to `login`.**

  **
  **

      public interface CredentialsProvider
      extends java.io.Serializable, javax.naming.Referenceable

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                               | Method and Description                                                                                                                                                                                                                                |
    |-------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Credentials`](../../javax/jcr/Credentials.md) | `getCredentials``(`[`Repository`](../../javax/jcr/Repository.md)` repository, java.lang.String workspaceName)`<br>Deprecated. <br>Gets credentials used to create a JCR session when no credentials are supplied to the `login` method of Repository. |

    - ### Methods inherited from interface javax.naming.Referenceable

      `getReference`

<!-- -->

- - ### Method Detail

    - #### getCredentials

          Credentials getCredentials(Repository repository,
                                     java.lang.String workspaceName)
                              throws java.lang.Exception

      Deprecated. 
      Gets credentials used to create a JCR session when no credentials are supplied to the `login` method of Repository.
      Parameters:
      `repository` - the repository; required

      `workspaceName` - the workspace, or null for the "default" workspace

      Returns:
      the Credentials, or null if unable to generate Credentials

      Throws:
      `java.lang.Exception` - if the operation fails

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

- **Prev Class**
- **[Next Class](OracleNamespaceRegistry.md)**

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
