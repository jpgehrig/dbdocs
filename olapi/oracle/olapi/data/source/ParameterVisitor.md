Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev Class](Parameter.md)
- [Next Class](Qualification.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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

oracle.olapi.data.source

## Class ParameterVisitor

- java.lang.Object

- - oracle.olapi.data.source.ParameterVisitor

<!-- -->

-

  ------------------------------------------------------------------------



      public abstract class ParameterVisitor
      extends java.lang.Object

  A visitor object that can execute operations on `Parameter` objects. A `ParameterVisitor` can implement polymorphic behavior without having access to the internal code of the `Parameter` subclasses.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `ParameterVisitor``()`      |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                                                        |
    |--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object` | `visitBooleanParameter``(`[`BooleanParameter`](BooleanParameter.md)` param, java.lang.Object context)`<br>Executes operations on the specified `BooleanParameter`.                                                            |
    | `java.lang.Object` | `visitDateParameter``(`[`DateParameter`](DateParameter.md)` param, java.lang.Object context)`<br>Executes operations on the specified `DateParameter`.                                                                        |
    | `java.lang.Object` | `visitNumberParameter``(`[`NumberParameter`](NumberParameter.md)` param, java.lang.Object context)`<br>Executes operations on the specified `NumberParameter`.                                                                |
    | `java.lang.Object` | `visitParameter``(`[`Parameter`](Parameter.md)` param, java.lang.Object context)`<br>Executes operations on any object that is a subclass of `Parameter`, which is useful when you do not need subclass-specific information. |
    | `java.lang.Object` | `visitStringParameter``(`[`StringParameter`](StringParameter.md)` param, java.lang.Object context)`<br>Executes operations on the specified `StringParameter`.                                                                |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### ParameterVisitor

          public ParameterVisitor()

  <!-- -->

  - ### Method Detail

    - #### visitParameter

          public java.lang.Object visitParameter(Parameter param,
                                                 java.lang.Object context)

      Executes operations on any object that is a subclass of `Parameter`, which is useful when you do not need subclass-specific information. The default implementation of this method returns `null`.
      Parameters:
      `param` - A `Parameter` object.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitStringParameter

          public java.lang.Object visitStringParameter(StringParameter param,
                                                       java.lang.Object context)

      Executes operations on the specified `StringParameter`. The default implementation of this method calls the `visitParameter` method.
      Parameters:
      `param` - A `StringParameter` object.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitDateParameter

          public java.lang.Object visitDateParameter(DateParameter param,
                                                     java.lang.Object context)

      Executes operations on the specified `DateParameter`. The default implementation of this method calls the `visitParameter` method.
      Parameters:
      `param` - A `DateParameter` object.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitBooleanParameter

          public java.lang.Object visitBooleanParameter(BooleanParameter param,
                                                        java.lang.Object context)

      Executes operations on the specified `BooleanParameter`. The default implementation of this method calls the `visitParameter` method.
      Parameters:
      `param` - A `BooleanParameter` object.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitNumberParameter

          public java.lang.Object visitNumberParameter(NumberParameter param,
                                                       java.lang.Object context)

      Executes operations on the specified `NumberParameter`. The default implementation of this method calls the `visitParameter` method.
      Parameters:
      `param` - A `NumberParameter` object.

      `context` - An `Object`.

      Returns:
      An `Object`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](Parameter.md)
- [Next Class](Qualification.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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
