Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database Advanced Queuing Java API Reference
19c**
E96513-01

- [Prev Class](ConnectionFactory.md)
- [Next Class](DeliveryMode.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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

javax.jms

## Interface ConnectionMetaData

- All Known Implementing Classes:
  [AQjmsConnectionMetaData](../../oracle/jms/AQjmsConnectionMetaData.md)

  ------------------------------------------------------------------------



      public interface ConnectionMetaData

  A `ConnectionMetaData` object provides information describing the `Connection` object.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type       | Method and Description                                                        |
    |-------------------------|-------------------------------------------------------------------------------|
    | `int`                   | `getJMSMajorVersion``()`<br>Gets the JMS major version number.                |
    | `int`                   | `getJMSMinorVersion``()`<br>Gets the JMS minor version number.                |
    | `java.lang.String`      | `getJMSProviderName``()`<br>Gets the JMS provider name.                       |
    | `java.lang.String`      | `getJMSVersion``()`<br>Gets the JMS API version.                              |
    | `java.util.Enumeration` | `getJMSXPropertyNames``()`<br>Gets an enumeration of the JMSX property names. |
    | `int`                   | `getProviderMajorVersion``()`<br>Gets the JMS provider major version number.  |
    | `int`                   | `getProviderMinorVersion``()`<br>Gets the JMS provider minor version number.  |
    | `java.lang.String`      | `getProviderVersion``()`<br>Gets the JMS provider version.                    |

<!-- -->

- - ### Method Detail

    - #### getJMSVersion

          java.lang.String getJMSVersion()
                                  throws JMSException

      Gets the JMS API version.
      Returns:
      the JMS API version

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to retrieve the metadata due to some internal error.

    <!-- -->

    - #### getJMSMajorVersion

          int getJMSMajorVersion()
                          throws JMSException

      Gets the JMS major version number.
      Returns:
      the JMS API major version number

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to retrieve the metadata due to some internal error.

    <!-- -->

    - #### getJMSMinorVersion

          int getJMSMinorVersion()
                          throws JMSException

      Gets the JMS minor version number.
      Returns:
      the JMS API minor version number

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to retrieve the metadata due to some internal error.

    <!-- -->

    - #### getJMSProviderName

          java.lang.String getJMSProviderName()
                                       throws JMSException

      Gets the JMS provider name.
      Returns:
      the JMS provider name

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to retrieve the metadata due to some internal error.

    <!-- -->

    - #### getProviderVersion

          java.lang.String getProviderVersion()
                                       throws JMSException

      Gets the JMS provider version.
      Returns:
      the JMS provider version

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to retrieve the metadata due to some internal error.

    <!-- -->

    - #### getProviderMajorVersion

          int getProviderMajorVersion()
                               throws JMSException

      Gets the JMS provider major version number.
      Returns:
      the JMS provider major version number

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to retrieve the metadata due to some internal error.

    <!-- -->

    - #### getProviderMinorVersion

          int getProviderMinorVersion()
                               throws JMSException

      Gets the JMS provider minor version number.
      Returns:
      the JMS provider minor version number

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to retrieve the metadata due to some internal error.

    <!-- -->

    - #### getJMSXPropertyNames

          java.util.Enumeration getJMSXPropertyNames()
                                              throws JMSException

      Gets an enumeration of the JMSX property names.
      Returns:
      an Enumeration of JMSX property names

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to retrieve the metadata due to some internal error.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database Advanced Queuing Java API Reference
19c**
E96513-01

- [Prev Class](ConnectionFactory.md)
- [Next Class](DeliveryMode.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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

Copyright © 2001, 2019, Oracle and/or its affiliates. All rights reserved.
