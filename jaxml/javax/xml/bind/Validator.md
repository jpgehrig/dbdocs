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

- **[Prev Class](ValidationException.md)**
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

**javax.xml.bind**

## **Interface Validator**

-

  ------------------------------------------------------------------------

  **
  **

      public interface Validator

  **The `Validator` class is responsible for controlling the validation of content trees during runtime.**
  **Three Forms of Validation
  **

  > **Unmarshal-Time Validation**
  > This form of validation enables a client application to receive information about validation errors and warnings detected while unmarshalling XML data into a Java content tree and is completely orthogonal to the other types of validation. To enable or disable it, see the javadoc for [`Unmarhaller.setValidating`](Unmarshaller.md). All JAXB Providers are required to support this operation.
  >
  > **On-Demand Validation**
  > This form of validation enables a client application to receive information about validation errors and warnings detected in the Java content tree. At any point, client applications can call the `Validator.validate` method on the Java content tree (or any sub-tree of it). All JAXB Providers are required to support this operation.
  >
  > **Fail-Fast Validation**
  > This form of validation enables a client application to receive immediate feedback about modifications to the Java content tree that violate type constraints on Java Properties as defined in the specification. JAXB Providers are not required support this type of validation. Of the JAXB Providers that do support this type of validation, some may require you to decide at schema compile time whether or not a client application will be allowed to request fail-fast validation at runtime.

  The `Validator` class is responsible for managing On-Demand Validation. The `Unmarshaller` class is responsible for managing Unmarshal-Time Validation during the unmarshal operations. Although there is no formal method of enabling validation during the marshal operations, the `Marshaller` may detect errors, which will be reported to the `ValidationEventHandler` registered on it.

  **Using the Default EventHandler**

  > If the client application does not set an event handler on their `Validator`, `Unmarshaller`, or `MArshaller` prior to calling the validate, unmarshal, or marshal methods, then a default event handler will receive notification of any errors or warnings encountered. The default event handler will cause the current operation to halt after encountering the first error or fatal error (but will attempt to continue after receiving warnings).

  **Handling Validation Events**

  > There are three ways to handle events encountered during the unmarshal, validate, and marshal operations:
  >
  > Use the default event handler
  > The default event handler will be used if you do not specify one via the `setEventHandler` API's on `Validator`, `Unmarshaller`, or `Marshaller`.
  >
  > Implement and register a custom event handler
  > Client applications that require sophisticated event processing can implement the `ValidationEventHandler` interface and register it with the `Unmarshaller` and/or `Validator`.
  >
  > Use the `ValidationEventCollector` utility
  > For convenience, a specialized event handler is provided that simply collects any `ValidationEvent` objects created during the unmarshal, validate, and marshal operations and returns them to the client application as a `java.util.Collection`.

  **Validation and Well-Formedness**

  > Validation events are handled differently depending on how the client application is configured to process them as described in the previous section. However, there are certain cases where a JAXB Provider indicates that it is no longer able to reliably detect and report errors. In these cases, the JAXB Provider will set the severity of the ValidationEvent to FATAL_ERROR to indicate that the unmarshal, validate, or marshal operations should be terminated. The default event handler and `ValidationEventCollector` utility class must terminate processing after being notified of a fatal error. Client applications that supply their own `ValidationEventHandler` should also terminate processing after being notified of a fatal error. If not, unexpected behaviour may occur.

  Since:
  JAXB1.0

  See Also:
  [`JAXBContext`](JAXBContext.md), [`Unmarshaller`](Unmarshaller.md), [`ValidationEventHandler`](ValidationEventHandler.md), [`ValidationEvent`](ValidationEvent.md), `util.ValidationEventCollector`

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                     | Method and Description                                                                                                                               |
    |-------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`ValidationEventHandler`](ValidationEventHandler.md) | `getEventHandler``()`<br>Return the current event handler or the default event handler if one hasn't been set.                                       |
    | `void`                                                | `setEventHandler``(`[`ValidationEventHandler`](ValidationEventHandler.md)` handler)`<br>Allow an application to register a validation event handler. |
    | `boolean`                                             | `validate``(java.lang.Object subrootObj)`<br>Validate the Java content tree starting at `subrootObj`.                                                |
    | `boolean`                                             | `validateRoot``(java.lang.Object rootObj)`<br>Validate the Java content tree rooted at `rootObj`.                                                    |

<!-- -->

- - ### Method Detail

    - #### setEventHandler

          void setEventHandler(ValidationEventHandler handler)
                        throws JAXBException

      Allow an application to register a validation event handler.
      The validation event handler will be called by the JAXB Provider if any validation errors are encountered during calls to `validate`. If the client application does not register a validation event handler before invoking the validate method, then validation events will be handled by the default event handler which will terminate the validate operation after the first error or fatal error is encountered.

      Parameters:
      `handler` - the validation event handler

      Throws:
      [`JAXBException`](JAXBException.md) - if an error was encountered while setting the event handler

    <!-- -->

    - #### getEventHandler

          ValidationEventHandler getEventHandler()
                                          throws JAXBException

      Return the current event handler or the default event handler if one hasn't been set.
      Returns:
      the current ValidationEventHandler or the default event handler if it hasn't been set

      Throws:
      [`JAXBException`](JAXBException.md) - if an error was encountered while getting the current event handler

    <!-- -->

    - #### validate

          boolean validate(java.lang.Object subrootObj)
                    throws JAXBException

      Validate the Java content tree starting at `subrootObj`.
      Client applications can use this method to validate Java content trees on-demand at runtime. This method can be used to validate any arbitrary subtree of the Java content tree. Global constraint checking **will not** be performed as part of this operation (i.e. ID/IDREF constraints).

      Parameters:
      `subrootObj` - the obj to begin validation at

      Returns:
      true if the subtree rooted at `subrootObj` is valid, false otherwise

      Throws:
      [`JAXBException`](JAXBException.md) - if any unexpected problem occurs during validation

      [`ValidationException`](ValidationException.md) - if the provider is unable to validate the content tree rooted at `subrootObj`

    <!-- -->

    - #### validateRoot

          boolean validateRoot(java.lang.Object rootObj)
                        throws JAXBException

      Validate the Java content tree rooted at `rootObj`.
      Client applications can use this method to validate Java content trees on-demand at runtime. This method is used to validate an entire Java content tree. Global constraint checking **will** be performed as part of this operation (i.e. ID/IDREF constraints).

      Parameters:
      `rootObj` - the root obj to begin validation at

      Returns:
      true if the tree rooted at `rootObj` is valid, false otherwise

      Throws:
      [`JAXBException`](JAXBException.md) - if any unexpected problem occurs during validation

      [`ValidationException`](ValidationException.md) - if the provider is unable to validate the content tree rooted at `rootObj`

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

- **[Prev Class](ValidationException.md)**
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
