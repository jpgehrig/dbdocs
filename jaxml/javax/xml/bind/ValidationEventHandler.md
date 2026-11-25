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

- **[Prev Class](ValidationEvent.md)**
- **[Next Class](ValidationEventLocator.md)**

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

**javax.xml.bind**

## **Interface ValidationEventHandler**

-

  ------------------------------------------------------------------------

  **
  **

      public interface ValidationEventHandler

  **A basic event handler interface for validation errors.**
  **If an application needs to implement customized event handling, it must implement this interface and then register it with either the [`Unmarshaller`](Unmarshaller.md), the [`Validator`](Validator.md), or the [`Marshaller`](Marshaller.md). The JAXB Provider will then report validation errors and warnings encountered during the unmarshal, marshal, and validate operations to these event handlers.**

  **Modifying the Java content tree within your event handler is undefined by the specification and may result in unexpected behaviour.**

  **Failing to return false from the `handleEvent` method after encountering a fatal error is undefined by the specification and may result in unexpected behavior.**

  **Default Event Handler**

  > See: [Validator javadocs](Validator.md)

  Since:
  JAXB1.0

  See Also:
  [`Validator`](Validator.md), [`ValidationEvent`](ValidationEvent.md), `javax.xml.bind.util.ValidationEventCollector`

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                     |
    |-------------------|----------------------------------------------------------------------------------------------------------------------------|
    | `boolean`         | `handleEvent``(`[`ValidationEvent`](ValidationEvent.md)` event)`<br>Receive notification of a validation warning or error. |

<!-- -->

- - ### Method Detail

    - #### handleEvent

          boolean handleEvent(ValidationEvent event)

      Receive notification of a validation warning or error. The ValidationEvent will have a [`ValidationEventLocator`](ValidationEventLocator.md) embedded in it that indicates where the error or warning occurred.
      Parameters:
      `event` - the encapsulated validation event information

      Returns:
      true if the JAXB Provider should attempt to continue validating after handling this warning/error, false otherwise

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

- **[Prev Class](ValidationEvent.md)**
- **[Next Class](ValidationEventLocator.md)**

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
