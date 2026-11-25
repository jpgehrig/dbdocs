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

- [Prev Class](AQjmsDestination.md)
- [Next Class](AQjmsDestinationProperty.md)

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

## Class AQjmsDestinationFactory

- java.lang.Object

- - oracle.jms.AQjmsDestinationFactory

<!-- -->

- All Implemented Interfaces:
  javax.naming.spi.ObjectFactory

  ------------------------------------------------------------------------



      public class AQjmsDestinationFactory
      extends java.lang.Object
      implements javax.naming.spi.ObjectFactory

  This is an Oracle class which implements `javax.naming.spi.ObjectFactory`. Factory class for producing JMS destination objects

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                   |
    |-------------------------------------------------------------------------------|
    | `AQjmsDestinationFactory``()`<br>Creates an `AQjmsDestinationFactory` object. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                                       |
    |--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object` | `getObjectInstance``(java.lang.Object obj, javax.naming.Name name, javax.naming.Context nameCtx, java.util.Hashtable environment)`<br>Creates a destination. |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### AQjmsDestinationFactory

          public AQjmsDestinationFactory()

      Creates an `AQjmsDestinationFactory` object.

  <!-- -->

  - ### Method Detail

    - #### getObjectInstance

          public java.lang.Object getObjectInstance(java.lang.Object obj,
                                                    javax.naming.Name name,
                                                    javax.naming.Context nameCtx,
                                                    java.util.Hashtable environment)
                                             throws JMSException

      Creates a destination. The destination is created using destination attributes obtained using `name` and `nameCtx` and table attributes obtained using `environment`.
      Specified by:
      `getObjectInstance` in interface `javax.naming.spi.ObjectFactory`

      Parameters:
      `obj` - a `javax.naming.Reference` indicating the destination class

      `name` - the location containing the destination attributes

      `nameCtx` - a `javax.naming.directory.DirContext` containing the following destination attributes at the above location:

      - `AQjmsConstants.LDAP_OWN_ATTR`
      - `AQjmsConstants.LDAP_NAM_ATTR`
      - `AQjmsConstants.LDAP_PTR_ATTR`
      - `AQjmsConstants.LDAP_GEN_ATTR`:
        - `"queuetype"` (`AQQueueProperty.NORMAL_QUEUE` or `AQQueueProperty.EXCEPTION_QUEUE`)
        - `"maxretries"`
        - `"retryinterval"`
        - `"rentention"` (retention time)

      `environment` - used to create an `InitialDirContext` containing the following table attributes at the location indicated by the above `AQjmsConstants.LDAP_PTR_ATTR` attribute:

      - `AQjmsConstants.LDAP_NAM_ATTR`
      - `AQjmsConstants.LDAP_GEN_ATTR`:
        - `"payloadtype"`
        - `"multiconsumers"` (`true` for a topic, `false` for a queue)

      Returns:
      a new destination object, or `null` if:

      - `obj` is invalid,
      - looking up the provided `name` in the provided `nameCtx` fails,
      - looking up the table attributes with the context created using `environment` fails, or
      - any of the `LDAP_`\*`_ATTR` attributes are not found

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a destination is not created for any reason other than those listed above (which result in a `null` return value).

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

- [Prev Class](AQjmsDestination.md)
- [Next Class](AQjmsDestinationProperty.md)

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
