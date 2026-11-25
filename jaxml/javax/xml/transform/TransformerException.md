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

- **[Prev Class](TransformerConfigurationException.md)**
- **[Next Class](TransformerFactory.md)**

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

**javax.xml.transform**

## **Class TransformerException**

- **java.lang.Object**

- - **java.lang.Throwable**

  - - **java.lang.Exception**

    - - **javax.xml.transform.TransformerException**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable**

  <!-- -->

  **Direct Known Subclasses:**
  **[TransformerConfigurationException](TransformerConfigurationException.md)**

  ------------------------------------------------------------------------

  **
  **

      public class TransformerException
      extends java.lang.Exception

  **This class specifies an exceptional condition that occured during the transformation process.**
  **See Also:**
  **[Serialized Form](../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                                                                                       |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `TransformerException``(java.lang.String message)`<br>Create a new TransformerException.                                                                                          |
    | `TransformerException``(java.lang.String message, `[`SourceLocator`](SourceLocator.md)` locator)`<br>Create a new TransformerException from a message and a Locator.              |
    | `TransformerException``(java.lang.String message, `[`SourceLocator`](SourceLocator.md)` locator, java.lang.Throwable e)`<br>Wrap an existing exception in a TransformerException. |
    | `TransformerException``(java.lang.String message, java.lang.Throwable e)`<br>Wrap an existing exception in a TransformerException.                                                |
    | `TransformerException``(java.lang.Throwable e)`<br>Create a new TransformerException wrapping an existing exception.                                                              |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                   | Method and Description                                                                                                                                                |
    |-------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Throwable`               | `getCause``()`<br>Returns the cause of this throwable or `null` if the cause is nonexistent or unknown.                                                               |
    | `java.lang.Throwable`               | `getException``()`<br>This method retrieves an exception that this exception wraps.                                                                                   |
    | `java.lang.String`                  | `getLocationAsString``()`<br>Get the location information as a string.                                                                                                |
    | [`SourceLocator`](SourceLocator.md) | `getLocator``()`<br>Method getLocator retrieves an instance of a SourceLocator object that specifies where an error occured.                                          |
    | `java.lang.String`                  | `getMessageAndLocation``()`<br>Get the error message with location information appended.                                                                              |
    | `java.lang.Throwable`               | `initCause``(java.lang.Throwable cause)`<br>Initializes the *cause* of this throwable to the specified value.                                                         |
    | `void`                              | `printStackTrace``()`<br>Print the the trace of methods from where the error originated.                                                                              |
    | `void`                              | `printStackTrace``(java.io.PrintStream s)`<br>Print the the trace of methods from where the error originated.                                                         |
    | `void`                              | `printStackTrace``(java.io.PrintWriter s)`<br>Print the the trace of methods from where the error originated.                                                         |
    | `void`                              | `setLocator``(`[`SourceLocator`](SourceLocator.md)` location)`<br>Method setLocator sets an instance of a SourceLocator object that specifies where an error occured. |

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getLocalizedMessage, getMessage, getStackTrace, getSuppressed, setStackTrace, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### TransformerException

          public TransformerException(java.lang.String message)

      Create a new TransformerException.
      Parameters:
      `message` - The error or warning message.

    <!-- -->

    - #### TransformerException

          public TransformerException(java.lang.Throwable e)

      Create a new TransformerException wrapping an existing exception.
      Parameters:
      `e` - The exception to be wrapped.

    <!-- -->

    - #### TransformerException

          public TransformerException(java.lang.String message,
                                      java.lang.Throwable e)

      Wrap an existing exception in a TransformerException.
      This is used for throwing processor exceptions before the processing has started.

      Parameters:
      `message` - The error or warning message, or null to use the message from the embedded exception.

      `e` - Any exception

    <!-- -->

    - #### TransformerException

          public TransformerException(java.lang.String message,
                                      SourceLocator locator)

      Create a new TransformerException from a message and a Locator.
      This constructor is especially useful when an application is creating its own exception from within a DocumentHandler callback.

      Parameters:
      `message` - The error or warning message.

      `locator` - The locator object for the error or warning.

    <!-- -->

    - #### TransformerException

          public TransformerException(java.lang.String message,
                                      SourceLocator locator,
                                      java.lang.Throwable e)

      Wrap an existing exception in a TransformerException.
      Parameters:
      `message` - The error or warning message, or null to use the message from the embedded exception.

      `locator` - The locator object for the error or warning.

      `e` - Any exception

  <!-- -->

  - ### Method Detail

    - #### getLocator

          public SourceLocator getLocator()

      Method getLocator retrieves an instance of a SourceLocator object that specifies where an error occured.
      Returns:
      A SourceLocator object, or null if none was specified.

    <!-- -->

    - #### setLocator

          public void setLocator(SourceLocator location)

      Method setLocator sets an instance of a SourceLocator object that specifies where an error occured.
      Parameters:
      `location` - A SourceLocator object, or null to clear the location.

    <!-- -->

    - #### getException

          public java.lang.Throwable getException()

      This method retrieves an exception that this exception wraps.
      Returns:
      An Throwable object, or null.

      See Also:
      `getCause()`

    <!-- -->

    - #### getCause

          public java.lang.Throwable getCause()

      Returns the cause of this throwable or `null` if the cause is nonexistent or unknown. (The cause is the throwable that caused this throwable to get thrown.)
      Overrides:
      `getCause` in class `java.lang.Throwable`

    <!-- -->

    - #### initCause

          public java.lang.Throwable initCause(java.lang.Throwable cause)

      Initializes the *cause* of this throwable to the specified value. (The cause is the throwable that caused this throwable to get thrown.)
      This method can be called at most once. It is generally called from within the constructor, or immediately after creating the throwable. If this throwable was created with `TransformerException(Throwable)` or `TransformerException(String,Throwable)`, this method cannot be called even once.

      Overrides:
      `initCause` in class `java.lang.Throwable`

      Parameters:
      `cause` - the cause (which is saved for later retrieval by the `getCause()` method). (A `null` value is permitted, and indicates that the cause is nonexistent or unknown.)

      Returns:
      a reference to this `Throwable` instance.

      Throws:
      `java.lang.IllegalArgumentException` - if `cause` is this throwable. (A throwable cannot be its own cause.)

      `java.lang.IllegalStateException` - if this throwable was created with `TransformerException(Throwable)` or `TransformerException(String,Throwable)`, or this method has already been called on this throwable.

    <!-- -->

    - #### getMessageAndLocation

          public java.lang.String getMessageAndLocation()

      Get the error message with location information appended.

    <!-- -->

    - #### getLocationAsString

          public java.lang.String getLocationAsString()

      Get the location information as a string.
      Returns:
      A string with location info, or null if there is no location information.

    <!-- -->

    - #### printStackTrace

          public void printStackTrace()

      Print the the trace of methods from where the error originated. This will trace all nested exception objects, as well as this object.
      Overrides:
      `printStackTrace` in class `java.lang.Throwable`

    <!-- -->

    - #### printStackTrace

          public void printStackTrace(java.io.PrintStream s)

      Print the the trace of methods from where the error originated. This will trace all nested exception objects, as well as this object.
      Overrides:
      `printStackTrace` in class `java.lang.Throwable`

      Parameters:
      `s` - The stream where the dump will be sent to.

    <!-- -->

    - #### printStackTrace

          public void printStackTrace(java.io.PrintWriter s)

      Print the the trace of methods from where the error originated. This will trace all nested exception objects, as well as this object.
      Overrides:
      `printStackTrace` in class `java.lang.Throwable`

      Parameters:
      `s` - The writer where the dump will be sent to.

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

- **[Prev Class](TransformerConfigurationException.md)**
- **[Next Class](TransformerFactory.md)**

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
