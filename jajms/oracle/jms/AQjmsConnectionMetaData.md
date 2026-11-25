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

- [Prev Class](AQjmsConnectionFactory.md)
- [Next Class](AQjmsConsumer.md)

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

oracle.jms

## Class AQjmsConnectionMetaData

- java.lang.Object

- - oracle.jms.AQjmsConnectionMetaData

<!-- -->

- All Implemented Interfaces:
  [ConnectionMetaData](../../javax/jms/ConnectionMetaData.md)

  ------------------------------------------------------------------------



      public class AQjmsConnectionMetaData
      extends java.lang.Object
      implements ConnectionMetaData

  This is an Oracle class which implements `javax.jms.ConnectionMetaData`. Class `AQjmsConnectionMetaData` represents the metadata information available for a JMS connection. This contains information like version number and vendor name of the JMS server to which a connection is created.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                      |
    |----------------------------------------------------------------------------------|
    | `AQjmsConnectionMetaData``()`<br>Creates a new `AQjmsConnectionMetaData` object. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type       | Method and Description                                                        |
    |-------------------------|-------------------------------------------------------------------------------|
    | `int`                   | `getJMSMajorVersion``()`<br>Gets the JMS major version number.                |
    | `int`                   | `getJMSMinorVersion``()`<br>Gets the JMS minor version number.                |
    | `java.lang.String`      | `getJMSProviderName``()`<br>Gets the JMS provider name.                       |
    | `java.lang.String`      | `getJMSVersion``()`<br>Gets the JMS version.                                  |
    | `java.util.Enumeration` | `getJMSXPropertyNames``()`<br>Gets an enumeration of the JMSX property names. |
    | `int`                   | `getProviderMajorVersion``()`<br>Gets the JMS provider major version number.  |
    | `int`                   | `getProviderMinorVersion``()`<br>Gets the JMS provider minor version number.  |
    | `java.lang.String`      | `getProviderVersion``()`<br>Gets the JMS provider version.                    |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### AQjmsConnectionMetaData

          public AQjmsConnectionMetaData()

      Creates a new `AQjmsConnectionMetaData` object.

  <!-- -->

  - ### Method Detail

    - #### getJMSVersion

          public java.lang.String getJMSVersion()
                                         throws JMSException

      Gets the JMS version.
      Specified by:
      [`getJMSVersion`](../../javax/jms/ConnectionMetaData.md) in interface [`ConnectionMetaData`](../../javax/jms/ConnectionMetaData.md)

      Returns:
      the JMS version

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the metadata is not retrieved due to some internal error.

    <!-- -->

    - #### getJMSMajorVersion

          public int getJMSMajorVersion()
                                 throws JMSException

      Gets the JMS major version number.
      Specified by:
      [`getJMSMajorVersion`](../../javax/jms/ConnectionMetaData.md) in interface [`ConnectionMetaData`](../../javax/jms/ConnectionMetaData.md)

      Returns:
      the JMS major version number

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the metadata is not retrieved due to some internal error.

    <!-- -->

    - #### getJMSMinorVersion

          public int getJMSMinorVersion()
                                 throws JMSException

      Gets the JMS minor version number.
      Specified by:
      [`getJMSMinorVersion`](../../javax/jms/ConnectionMetaData.md) in interface [`ConnectionMetaData`](../../javax/jms/ConnectionMetaData.md)

      Returns:
      the JMS minor version number

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the metadata is not retrieved due to some internal error.

    <!-- -->

    - #### getJMSProviderName

          public java.lang.String getJMSProviderName()
                                              throws JMSException

      Gets the JMS provider name.
      Specified by:
      [`getJMSProviderName`](../../javax/jms/ConnectionMetaData.md) in interface [`ConnectionMetaData`](../../javax/jms/ConnectionMetaData.md)

      Returns:
      the JMS provider name

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the metadata is not retrieved due to some internal error.

    <!-- -->

    - #### getProviderVersion

          public java.lang.String getProviderVersion()
                                              throws JMSException

      Gets the JMS provider version.
      Specified by:
      [`getProviderVersion`](../../javax/jms/ConnectionMetaData.md) in interface [`ConnectionMetaData`](../../javax/jms/ConnectionMetaData.md)

      Returns:
      the JMS provider version

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the metadata is not retrieved due to some internal error.

    <!-- -->

    - #### getProviderMajorVersion

          public int getProviderMajorVersion()
                                      throws JMSException

      Gets the JMS provider major version number.
      Specified by:
      [`getProviderMajorVersion`](../../javax/jms/ConnectionMetaData.md) in interface [`ConnectionMetaData`](../../javax/jms/ConnectionMetaData.md)

      Returns:
      the JMS provider major version number

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the metadata is not retrieved due to some internal error.

    <!-- -->

    - #### getProviderMinorVersion

          public int getProviderMinorVersion()
                                      throws JMSException

      Gets the JMS provider minor version number.
      Specified by:
      [`getProviderMinorVersion`](../../javax/jms/ConnectionMetaData.md) in interface [`ConnectionMetaData`](../../javax/jms/ConnectionMetaData.md)

      Returns:
      the JMS provider minor version number

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the metadata is not retrieved due to some internal error.

    <!-- -->

    - #### getJMSXPropertyNames

          public java.util.Enumeration getJMSXPropertyNames()
                                                     throws JMSException

      Gets an enumeration of the JMSX property names.
      Specified by:
      [`getJMSXPropertyNames`](../../javax/jms/ConnectionMetaData.md) in interface [`ConnectionMetaData`](../../javax/jms/ConnectionMetaData.md)

      Returns:
      an enumeration of JMSX property names

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the metadata is not retrieved due to some internal error.

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

- [Prev Class](AQjmsConnectionFactory.md)
- [Next Class](AQjmsConsumer.md)

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
