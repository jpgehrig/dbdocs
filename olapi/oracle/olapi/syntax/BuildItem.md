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

- [Prev Class](BuildCommand.md)
- [Next Class](BuildProcess.md)

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

## Class BuildItem

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - oracle.olapi.syntax.BuildItem

<!-- -->

-

  ------------------------------------------------------------------------



      public final class BuildItem
      extends SyntaxObject

  A `SyntaxObject` that specifies a `Buildable` object and optionally a `BuildSpecification`, or a system change number (SCN), or both. An SCN identifies the state of the source data as of a particular moment when the database recorded a change to the source table. For information on obtaining system change numbers, see *Oracle Database SQL Language Reference*.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                      |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `BuildItem``(`[`Buildable`](Buildable.md)` obj)`<br>Creates a `BuildItem` for a `Buildable` object.                                                                                                                                              |
    | `BuildItem``(`[`Buildable`](Buildable.md)` obj, `[`BuildSpecification`](BuildSpecification.md)` inlineSpec)`<br>Creates a `BuildItem` for a `Buildable` object, using the specified `BuildSpecification`.                                        |
    | `BuildItem``(`[`Buildable`](Buildable.md)` obj, `[`BuildSpecification`](BuildSpecification.md)` inlineSpec, long scn)`<br>Creates a `BuildItem` for a `Buildable` object, using the specified `BuildSpecification` and using data as of the SCN. |
    | `BuildItem``(`[`Buildable`](Buildable.md)` obj, long scn)`<br>Creates a `BuildItem` for a `Buildable` object, using data as of the SCN.                                                                                                          |
    | `BuildItem``(`[`Buildable`](Buildable.md)` obj, java.lang.String buildName)`<br>Creates a `BuildItem` for a `Buildable` object, using the named `BuildSpecification`.                                                                            |
    | `BuildItem``(`[`Buildable`](Buildable.md)` obj, java.lang.String buildName, long scn)`<br>Creates a `BuildItem` for a `Buildable` object, using the named `BuildSpecification` and using data as of the SCN.                                     |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                             | Method and Description                                                                                                                                                                                                    |
    |-----------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `long`                                        | `getAsOfSCN``()`<br>Gets the system change number (SCN) at which to apply the build.                                                                                                                                      |
    | [`Buildable`](Buildable.md)                   | `getBuildObject``()`<br>Gets the `Buildable` object that is associated with this `BuildItem`.                                                                                                                             |
    | `java.lang.String`                            | `getBuildObjectID``()`<br>Gets the ID of the `Buildable` object that is associated with this `BuildItem`.                                                                                                                 |
    | `java.lang.String`                            | `getBuildSpecName``()`<br>Gets the name of the `BuildSpecification` for a `BuildItem` that was created with the `BuildItem(BaseMetadataObjectReference obj, String buildName)` constructor.                               |
    | [`BuildSpecification`](BuildSpecification.md) | `getInlineBuildSpecification``()`<br>Gets the `BuildSpecification` for a `BuildItem` that was created with the `BuildItem(BaseMetadataObjectReference obj, BuildSpecification inlineSpec)` constructor.                   |
    | `java.lang.Object`                            | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitBuildItem` method of the `SyntaxObjectVisitor` and passes that method this `BuildItem` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### BuildItem

          public BuildItem(Buildable obj)

      Creates a `BuildItem` for a `Buildable` object.
      Parameters:
      `obj` - The `MdmCube` or `MdmPrimaryDimension` to build.

    <!-- -->

    - #### BuildItem

          public BuildItem(Buildable obj,
                           long scn)

      Creates a `BuildItem` for a `Buildable` object, using data as of the SCN.
      Parameters:
      `obj` - The `MdmCube` or `MdmPrimaryDimension` to build.

      `scn` - A `long` value that specifies the SCN at which to load data.

    <!-- -->

    - #### BuildItem

          public BuildItem(Buildable obj,
                           java.lang.String buildName)

      Creates a `BuildItem` for a `Buildable` object, using the named `BuildSpecification`.
      Parameters:
      `obj` - The `MdmCube` to build.

      `buildName` - A `String` that contains the name of a `BuildSpecification` contained by the `AWCubeOrganization` for the `MdmCube`.

    <!-- -->

    - #### BuildItem

          public BuildItem(Buildable obj,
                           java.lang.String buildName,
                           long scn)

      Creates a `BuildItem` for a `Buildable` object, using the named `BuildSpecification` and using data as of the SCN.
      Parameters:
      `obj` - The `MdmCube` to build.

      `buildName` - A `String` that contains the name of a `BuildSpecification` contained by the `AWCubeOrganization` for the `MdmCube`.

      `scn` - A `long` value that specifies the SCN at which to load data.

    <!-- -->

    - #### BuildItem

          public BuildItem(Buildable obj,
                           BuildSpecification inlineSpec)

      Creates a `BuildItem` for a `Buildable` object, using the specified `BuildSpecification`.
      Parameters:
      `obj` - The `MdmCube` or `MdmPrimaryDimension` to build.

      `inlineSpec` - A `BuildSpecification` that contains the `BuildCommand` objects to use.

    <!-- -->

    - #### BuildItem

          public BuildItem(Buildable obj,
                           BuildSpecification inlineSpec,
                           long scn)

      Creates a `BuildItem` for a `Buildable` object, using the specified `BuildSpecification` and using data as of the SCN.
      Parameters:
      `obj` - The `MdmCube` or `MdmPrimaryDimension` to build.

      `inlineSpec` - A `BuildSpecification` that contains the `BuildCommand` objects to use.

      `scn` - A `long` value that specifies the SCN at which to load data.

  <!-- -->

  - ### Method Detail

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitBuildItem` method of the `SyntaxObjectVisitor` and passes that method this `BuildItem` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitBuildItem` method.

    <!-- -->

    - #### getBuildSpecName

          public java.lang.String getBuildSpecName()

      Gets the name of the `BuildSpecification` for a `BuildItem` that was created with the `BuildItem(BaseMetadataObjectReference obj, String buildName)` constructor. or `BuildItem(Buildable obj, String buildName)` constructor.
      Returns:
      A `String` that contains the name of the `BuildSpecification` associated with this `BuildItem`.

    <!-- -->

    - #### getBuildObject

          public Buildable getBuildObject()

      Gets the `Buildable` object that is associated with this `BuildItem`.
      Returns:
      The `Buildable` object associated with this `BuildItem`.

    <!-- -->

    - #### getBuildObjectID

          public java.lang.String getBuildObjectID()

      Gets the ID of the `Buildable` object that is associated with this `BuildItem`.
      Returns:
      A `String` that contains the ID of the `Buildable` object associated with this `BuildItem`.

    <!-- -->

    - #### getInlineBuildSpecification

          public BuildSpecification getInlineBuildSpecification()

      Gets the `BuildSpecification` for a `BuildItem` that was created with the `BuildItem(BaseMetadataObjectReference obj, BuildSpecification inlineSpec)` constructor. or `BuildItem(Buildable obj, BuildSpecification inlineSpec)`
      Returns:
      The `BuildSpecification` associated with this `BuildItem`.

    <!-- -->

    - #### getAsOfSCN

          public long getAsOfSCN()

      Gets the system change number (SCN) at which to apply the build. If the SCN is 0, then the build process does not use an SCN. If the SCN is greater than 0, then the build process executes a `LoadCommand` as of the SCN.
      Returns:
      A `long` that is the SCN of this `BuildItem`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](BuildCommand.md)
- [Next Class](BuildProcess.md)

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
