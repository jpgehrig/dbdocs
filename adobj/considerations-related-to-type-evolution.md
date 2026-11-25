The following sections contain design considerations relating to type evolution.

This section contains the following topics:

- Pushing a Type Change Out to Clients

- About Changing Default Constructors

- About Altering the FINAL Property of a Type

### 9.11.1 Pushing a Type Change Out to Clients

Once a type has evolved on the server side, all client applications using this type need to make the necessary changes to structures associated with the type. You can do this with OTT/JPUB.

You also may need to make programmatic changes associated with the structural change. After making these changes, you must recompile your application and relink.

Types may be altered between releases of a third-party application. To inform client applications that they need to recompile to become compatible with the latest release of the third-party application, you can have the clients call a release-oriented compatibility initialization function.

This function could take as input a string that tells it which release the client application is working with. If the release string mismatches with the latest version, an error is generated. The client application must then change the release string as part of the changes required to become compatible with the latest release.

For example:

    FUNCTION compatibility_init(
     rel IN VARCHAR2, errmsg OUT VARCHAR2)
    RETURN NUMBER;

where:

- `rel` is a release string that is chosen by the product, such as, `'Release 10.1'`

- `errmsg` is any error message that may need to be returned

- The function returns `0` on success and a nonzero value on error

### 9.11.2 About Changing Default Constructors

When a type is altered, its default, system-defined constructors need to be changed in order (for example) to include newly added attributes in the parameter list. If you are using default constructors, you need to modify their invocations in your program in order for the calls to compile.

You can avoid having to modify constructor calls if you define your own constructor functions instead of using the system-defined default ones. See "[Advantages of User-Defined Constructors](system-defined-and-user-defined-constructors.md)".

### 9.11.3 About Altering the FINAL Property of a Type

When you alter a type `T1` from `FINAL` to `NOT FINAL`, any attribute of type `T1` in the client program changes from being an inlined structure to a pointer to `T1`. This means that you need to change the program to use dereferencing when this attribute is accessed.

Conversely, when you alter a type from `NOT FINAL` to `FINAL`, the attributes of that type change from being pointers to inlined structures.

For example, say that you have the types `T1(a int)` and `T2(b T1)`, where `T1`'s property is `FINAL`. The C/JAVA structure corresponding to `T2` is `T2(T1 b)`. But if you change `T1`'s property to `NOT FINAL`, then `T2`'s structure becomes `T2(T1 *b)`.
