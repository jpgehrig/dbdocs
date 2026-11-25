Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database Globalization Development Kit Java API Reference
19c**
E96350-01

- Prev Class
- [Next Class](LocaleMapper.md)

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

oracle.i18n.util

## Class DualInputStreamBuilder

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.i18n.util.DualInputStreamBuilder

<!-- -->

-

  ------------------------------------------------------------------------



      public class DualInputStreamBuilder
      extends Object

  The `DualInputStreamBuilder` class generates two `InputStream` wrapper objects for one `InputStream` source.
  Use this class when two independent stream operations are required for one `InputStream` source. Usually one stream is for temporary use. For example, one stream detects the language and character set for the input stream and another stream is used for the real purpose.

  TIPS: Close either one of the `InputStream` objects as soon as the operation is completed.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                    |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `DualInputStreamBuilder``(`[`InputStream`](http://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` in)`<br>Constructs this object with the source `InputStream` object.           |
    | `DualInputStreamBuilder``(`[`InputStream`](http://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` in, int size)`<br>Constructs this object with the source `InputStream` object. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                   | Method and Description                                                 |
    |-----------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|
    | [`InputStream`](http://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true) | `getFirstInputStream``()`<br>Returns the first `InputStream` object.   |
    | [`InputStream`](http://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true) | `getSecondInputStream``()`<br>Returns the second `InputStream` object. |

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Constructor Detail

    - #### DualInputStreamBuilder

          public DualInputStreamBuilder(InputStream in,
                                        int size)

      Constructs this object with the source `InputStream` object.
      Parameters:
      `in` - `InputStream` object

      `size` - the buffer size

    <!-- -->

    - #### DualInputStreamBuilder

          public DualInputStreamBuilder(InputStream in)

      Constructs this object with the source `InputStream` object.
      Parameters:
      `in` - `InputStream` object

  <!-- -->

  - ### Method Detail

    - #### getFirstInputStream

          public InputStream getFirstInputStream()

      Returns the first `InputStream` object.
      Returns:
      the first `InputStream` object

    <!-- -->

    - #### getSecondInputStream

          public InputStream getSecondInputStream()

      Returns the second `InputStream` object.
      Returns:
      the second `InputStream` object

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database Globalization Development Kit Java API Reference
19c**
E96350-01

- Prev Class
- [Next Class](LocaleMapper.md)

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

Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
