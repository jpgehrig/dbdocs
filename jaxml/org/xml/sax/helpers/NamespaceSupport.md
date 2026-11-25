Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](LocatorImpl.md)**
- **[Next Class](ParserAdapter.md)**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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

**org.xml.sax.helpers**

## **Class NamespaceSupport**

- **java.lang.Object**

- - **org.xml.sax.helpers.NamespaceSupport**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class NamespaceSupport
      extends java.lang.Object

  **Encapsulate Namespace logic for use by SAX drivers.**
  > ***This module, both source code and documentation, is in the Public Domain, and comes with **NO WARRANTY**.***

  **This class encapsulates the logic of Namespace processing: it tracks the declarations currently in force for each context and automatically processes qualified XML 1.0 names into their Namespace parts; it can also be used in reverse for generating XML 1.0 from Namespaces.**

  **Namespace support objects are reusable, but the reset method must be invoked between each session.**

  **Here is a simple session:**

       String parts[] = new String[3];
       NamespaceSupport support = new NamespaceSupport();

       support.pushContext();
       support.declarePrefix("", "http://www.w3.org/1999/xhtml");
       support.declarePrefix("dc", "http://www.purl.org/dc#");

       String parts[] = support.processName("p", parts, false);
       System.out.println("Namespace URI: " + parts[0]);
       System.out.println("Local name: " + parts[1]);
       System.out.println("Raw name: " + parts[2]);

       String parts[] = support.processName("dc:title", parts, false);
       System.out.println("Namespace URI: " + parts[0]);
       System.out.println("Local name: " + parts[1]);
       System.out.println("Raw name: " + parts[2]);

       support.popContext();


  **Note that this class is optimized for the use case where most elements do not contain Namespace declarations: if the same prefix/URI mapping is repeated for each context (for example), this class will be somewhat less efficient.**

  **Since:**
  **SAX 2.0**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description                       |
    |---------------------------|---------------------------------------------|
    | `static java.lang.String` | `XMLNS`<br>The XML Namespace as a constant. |

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                      |
    |------------------------------------------------------------------|
    | `NamespaceSupport``()`<br>Create a new Namespace support object. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type       | Method and Description                                                                                                |
    |-------------------------|-----------------------------------------------------------------------------------------------------------------------|
    | `boolean`               | `declarePrefix``(java.lang.String prefix, java.lang.String uri)`<br>Declare a Namespace prefix.                       |
    | `java.util.Enumeration` | `getDeclaredPrefixes``()`<br>Return an enumeration of all prefixes declared in this context.                          |
    | `java.lang.String`      | `getPrefix``(java.lang.String uri)`<br>Return one of the prefixes mapped to a Namespace URI.                          |
    | `java.util.Enumeration` | `getPrefixes``()`<br>Return an enumeration of all prefixes currently declared.                                        |
    | `java.util.Enumeration` | `getPrefixes``(java.lang.String uri)`<br>Return an enumeration of all prefixes currently declared for a URI.          |
    | `java.lang.String`      | `getURI``(java.lang.String prefix)`<br>Look up a prefix and get the currently-mapped Namespace URI.                   |
    | `void`                  | `popContext``()`<br>Revert to the previous Namespace context.                                                         |
    | `java.lang.String[]`    | `processName``(java.lang.String qName, java.lang.String[] parts, boolean isAttribute)`<br>Process a raw XML 1.0 name. |
    | `void`                  | `pushContext``()`<br>Start a new Namespace context.                                                                   |
    | `void`                  | `reset``()`<br>Reset this Namespace support object for reuse.                                                         |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### XMLNS

          public static final java.lang.String XMLNS

      The XML Namespace as a constant.
      This is the Namespace URI that is automatically mapped to the "xml" prefix.

      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### NamespaceSupport

          public NamespaceSupport()

      Create a new Namespace support object.

  <!-- -->

  - ### Method Detail

    - #### reset

          public void reset()

      Reset this Namespace support object for reuse.
      It is necessary to invoke this method before reusing the Namespace support object for a new session.

    <!-- -->

    - #### pushContext

          public void pushContext()

      Start a new Namespace context.
      Normally, you should push a new context at the beginning of each XML element: the new context will automatically inherit the declarations of its parent context, but it will also keep track of which declarations were made within this context.

      The Namespace support object always starts with a base context already in force: in this context, only the "xml" prefix is declared.

      See Also:
      `popContext()`

    <!-- -->

    - #### popContext

          public void popContext()

      Revert to the previous Namespace context.
      Normally, you should pop the context at the end of each XML element. After popping the context, all Namespace prefix mappings that were previously in force are restored.

      You must not attempt to declare additional Namespace prefixes after popping a context, unless you push another context first.

      See Also:
      `pushContext()`

    <!-- -->

    - #### declarePrefix

          public boolean declarePrefix(java.lang.String prefix,
                                       java.lang.String uri)

      Declare a Namespace prefix.
      This method declares a prefix in the current Namespace context; the prefix will remain in force until this context is popped, unless it is shadowed in a descendant context.

      To declare a default Namespace, use the empty string. The prefix must not be "xml" or "xmlns".

      Note that you must *not* declare a prefix after you've pushed and popped another Namespace.

      Note that there is an asymmetry in this library: while `getPrefix` will not return the default "" prefix, even if you have declared one; to check for a default prefix, you have to look it up explicitly using `getURI`. This asymmetry exists to make it easier to look up prefixes for attribute names, where the default prefix is not allowed.

      Parameters:
      `prefix` - The prefix to declare, or null for the empty string.

      `uri` - The Namespace URI to associate with the prefix.

      Returns:
      true if the prefix was legal, false otherwise

      See Also:
      `processName(java.lang.String, java.lang.String[], boolean)`, `getURI(java.lang.String)`, `getPrefix(java.lang.String)`

    <!-- -->

    - #### processName

          public java.lang.String[] processName(java.lang.String qName,
                                                java.lang.String[] parts,
                                                boolean isAttribute)

      Process a raw XML 1.0 name.
      This method processes a raw XML 1.0 name in the current context by removing the prefix and looking it up among the prefixes currently declared. The return value will be the array supplied by the caller, filled in as follows:

      parts\[0\]
      The Namespace URI, or an empty string if none is in use.

      parts\[1\]
      The local name (without prefix).

      parts\[2\]
      The original raw name.

      All of the strings in the array will be internalized. If the raw name has a prefix that has not been declared, then the return value will be null.

      Note that attribute names are processed differently than element names: an unprefixed element name will received the default Namespace (if any), while an unprefixed element name will not.

      Parameters:
      `qName` - The raw XML 1.0 name to be processed.

      `parts` - An array supplied by the caller, capable of holding at least three members.

      `isAttribute` - A flag indicating whether this is an attribute name (true) or an element name (false).

      Returns:
      The supplied array holding three internalized strings representing the Namespace URI (or empty string), the local name, and the raw XML 1.0 name; or null if there is an undeclared prefix.

      See Also:
      `declarePrefix(java.lang.String, java.lang.String)`, `String.intern()`

    <!-- -->

    - #### getURI

          public java.lang.String getURI(java.lang.String prefix)

      Look up a prefix and get the currently-mapped Namespace URI.
      This method looks up the prefix in the current context. Use the empty string ("") for the default Namespace.

      Parameters:
      `prefix` - The prefix to look up.

      Returns:
      The associated Namespace URI, or null if the prefix is undeclared in this context.

      See Also:
      `getPrefix(java.lang.String)`, `getPrefixes()`

    <!-- -->

    - #### getPrefixes

          public java.util.Enumeration getPrefixes()

      Return an enumeration of all prefixes currently declared.
      **Note:** if there is a default prefix, it will not be returned in this enumeration; check for the default prefix using the `getURI` with an argument of "".

      Returns:
      An enumeration of all prefixes declared in the current context except for the empty (default) prefix.

      See Also:
      `getDeclaredPrefixes()`, `getURI(java.lang.String)`

    <!-- -->

    - #### getPrefix

          public java.lang.String getPrefix(java.lang.String uri)

      Return one of the prefixes mapped to a Namespace URI.
      If more than one prefix is currently mapped to the same URI, this method will make an arbitrary selection; if you want all of the prefixes, use the `getPrefixes()` method instead.

      **Note:** this will never return the empty (default) prefix; to check for a default prefix, use the `getURI` method with an argument of "".

      Parameters:
      `uri` - The Namespace URI.

      Returns:
      One of the prefixes currently mapped to the URI supplied, or null if none is mapped or if the URI is assigned to the default Namespace.

      See Also:
      `getPrefixes(java.lang.String)`, `getURI(java.lang.String)`

    <!-- -->

    - #### getPrefixes

          public java.util.Enumeration getPrefixes(java.lang.String uri)

      Return an enumeration of all prefixes currently declared for a URI.
      This method returns prefixes mapped to a specific Namespace URI. The xml: prefix will be included. If you want only one prefix that's mapped to the Namespace URI, and you don't care which one you get, use the `getPrefix` method instead.

      **Note:** the empty (default) prefix is *never* included in this enumeration; to check for the presence of a default Namespace, use the `getURI` method with an argument of "".

      Parameters:
      `uri` - The Namespace URI.

      Returns:
      An enumeration of all prefixes declared in the current context.

      See Also:
      `getPrefix(java.lang.String)`, `getDeclaredPrefixes()`, `getURI(java.lang.String)`

    <!-- -->

    - #### getDeclaredPrefixes

          public java.util.Enumeration getDeclaredPrefixes()

      Return an enumeration of all prefixes declared in this context.
      The empty (default) prefix will be included in this enumeration; note that this behaviour differs from that of `getPrefix(java.lang.String)` and `getPrefixes()`.

      Returns:
      An enumeration of all prefixes declared in this context.

      See Also:
      `getPrefixes()`, `getURI(java.lang.String)`

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](LocatorImpl.md)**
- **[Next Class](ParserAdapter.md)**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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

**org.xml.sax, org.xml.sax.ext, and org.xml.sax.helpers are SAX packages, and are in the public domain. See <http://www.saxproject.org>.**
