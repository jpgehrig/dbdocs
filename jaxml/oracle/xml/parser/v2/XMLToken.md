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

- **[Prev Class](XMLText.md)**
- **[Next Class](XMLTokenizer.md)**

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

**oracle.xml.parser.v2**

## **Interface XMLToken**

-

  ------------------------------------------------------------------------

  **
  **

      public interface XMLToken

  **Basic interface for XMLToken**
  **All XMLParser applications with Tokenizer feature must implement this interface. The interface has to be registered using `XMLTokenizer` method `setTokenHandler(XMLToken handler)`.**

  **If XMLtoken handler != null then for each registered and found token the parser calls the XMLToken call-back method `token(int token, String value)`. During tokenizing the parser doesn't validate the document and doesn't include/read internal/external entities. If XMLtoken handler == null then the parser parses as usual.**

  **A request for XML token is registered (on/off) using XMLParser method `setToken (int token, boolean set)`. The requests could be registered during the parsing (from inside the call-back method) as well.**

  **The XML tokens are defined as public constants in `XMLToken` interface. They correspond to the XML syntax variables from W3C XML Syntax Specification.**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description                                                                                                                                                             |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static int`      | `AttListDecl`<br>AttListDecl ::= '\<' '!'                                                                                                                                         |
    | `static int`      | `AttName`<br>AttName ::= Name                                                                                                                                                     |
    | `static int`      | `Attribute`<br>Attribute ::= AttName Eq AttValue                                                                                                                                  |
    | `static int`      | `AttValue`<br>AttValue ::= '"' (\[^\<&"\] \| Reference)\* '"' \| "'" (\[^\<&'\] \| Reference)\* "'"                                                                               |
    | `static int`      | `CDSect`<br>CDSect ::= CDStart CData CDEnd CDStart ::= '\<' '!'                                                                                                                   |
    | `static int`      | `CharData`<br>CharData ::= \[^\<&\]\* - (\[^\<&\]\* '\]\]\>' \[^\<&\]\*)                                                                                                          |
    | `static int`      | `Comment`<br>Comment ::= '\<' '!'                                                                                                                                                 |
    | `static int`      | `DTDName`<br>DTDName ::= name                                                                                                                                                     |
    | `static int`      | `ElemDeclName`<br>ElemDeclName ::= name                                                                                                                                           |
    | `static int`      | `elementdecl`<br>elementdecl ::= '\<' '!                                                                                                                                          |
    | `static int`      | `EmptyElemTag`<br>EmptyElemTag ::= '\<' STagName (S Attribute)\* S?                                                                                                               |
    | `static int`      | `EntityDecl`<br>EntityDecl ::= '\<' '!'                                                                                                                                           |
    | `static int`      | `EntityDeclName`<br>EntityValue ::= '"' (\[^%&"\] \| PEReference \| Reference)\* '"' \| "'" (\[^%&'\] \| PEReference \| Reference)\* "'"                                          |
    | `static int`      | `EntityValue`<br>EntityDeclName ::= Name                                                                                                                                          |
    | `static int`      | `ETag`<br>ETag ::= '\<' '/' ETagName S?                                                                                                                                           |
    | `static int`      | `ETagName`<br>ETagName ::= Name                                                                                                                                                   |
    | `static int`      | `ExternalID`<br>ExternalID ::= 'SYSTEM' S SystemLiteral \| 'PUBLIC' S PubidLiteral S SystemLiteral                                                                                |
    | `static int`      | `NotationDecl`<br>NotationDecl ::= '\<' '!                                                                                                                                        |
    | `static int`      | `PI`<br>PI ::= '\<' '?'                                                                                                                                                           |
    | `static int`      | `PITarget`<br>PITarget ::= Name - (('X' \| 'x') ('M' \| 'm') ('L' \| 'l'))                                                                                                        |
    | `static int`      | `Reference`<br>Reference ::= EntityRef \| CharRef \| PEReference EntityRef ::= '&' Name ';' PEReference ::= '%' Name ';' CharRef ::= '&#' \[0-9\]+ ';' \| '&#x' \[0-9a-fA-F\]+ '; |
    | `static int`      | `STag`<br>STag ::= '\<' STagName (S Attribute)\* S?                                                                                                                               |
    | `static int`      | `STagName`<br>STagName ::= Name                                                                                                                                                   |
    | `static int`      | `TextDecl`<br>TextDecl ::= '\<' '?'                                                                                                                                               |
    | `static int`      | `XMLDecl`<br>XMLDecl ::= '\<' '?'                                                                                                                                                 |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                          |
    |-------------------|---------------------------------------------------------------------------------|
    | `void`            | `token``(int token, java.lang.String value)`<br>The interface call-back method. |

<!-- -->

- - ### Field Detail

    - #### STag

          static final int STag

      STag ::= '\<' STagName (S Attribute)\* S? '\>'

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### EmptyElemTag

          static final int EmptyElemTag

      EmptyElemTag ::= '\<' STagName (S Attribute)\* S? '/' '\>'

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### STagName

          static final int STagName

      STagName ::= Name

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### AttValue

          static final int AttValue

      AttValue ::= '"' (\[^\<&"\] \| Reference)\* '"'

      \| "'" (\[^\<&'\] \| Reference)\* "'"

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### AttName

          static final int AttName

      AttName ::= Name

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### Attribute

          static final int Attribute

      Attribute ::= AttName Eq AttValue

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ETag

          static final int ETag

      ETag ::= '\<' '/' ETagName S? '\>'

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ETagName

          static final int ETagName

      ETagName ::= Name

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### CharData

          static final int CharData

      CharData ::= \[^\<&\]\* - (\[^\<&\]\* '\]\]\>' \[^\<&\]\*)

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### Comment

          static final int Comment

      Comment ::= '\<' '!' '--' ((Char - '-') \| ('-' (Char - '-')))\* '--\>'

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### Reference

          static final int Reference

      Reference ::= EntityRef \| CharRef \| PEReference

      EntityRef ::= '&' Name ';'

      PEReference ::= '%' Name ';'

      CharRef ::= '&#' \[0-9\]+ ';' \| '&#x' \[0-9a-fA-F\]+ ';

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### CDSect

          static final int CDSect

      CDSect ::= CDStart CData CDEnd

      CDStart ::= '\<' '!' '\[CDATA\['

      CData ::= (Char\* - (Char\* '\]\]\>' Char\*))

      CDEnd ::= '\]\]\>'

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### PI

          static final int PI

      PI ::= '\<' '?' PITarget (S (Char\* - (Char\* '?\>' Char\*)))? '?' '\>'

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### PITarget

          static final int PITarget

      PITarget ::= Name - (('X' \| 'x') ('M' \| 'm') ('L' \| 'l'))

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### XMLDecl

          static final int XMLDecl

      XMLDecl ::= '\<' '?' 'xml' VersionInfo EncodingDecl? SDDecl? S? '?' '\>'

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### TextDecl

          static final int TextDecl

      TextDecl ::= '\<' '?' 'xml' VersionInfo? EncodingDecl S? '?\>'

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### DTDName

          static final int DTDName

      DTDName ::= name

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### AttListDecl

          static final int AttListDecl

      AttListDecl ::= '\<' '!' 'ATTLIST' S Name AttDef\* S? '\>'

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### elementdecl

          static final int elementdecl

      elementdecl ::= '\<' '!ELEMENT' S ElemDeclName S contentspec S? '\>'

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ElemDeclName

          static final int ElemDeclName

      ElemDeclName ::= name

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### EntityDecl

          static final int EntityDecl

      EntityDecl ::= '\<' '!' ENTITY' S EntityDeclName S EntityDef S? '\>'

      \| '\<' '!' ENTITY' S '%' S EntityDeclName S PEDef S? '\>'

      EntityDef ::= EntityValue \| (ExternalID NDataDecl?)

      PEDef ::= EntityValue \| ExternalID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### EntityValue

          static final int EntityValue

      EntityDeclName ::= Name

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### EntityDeclName

          static final int EntityDeclName

      EntityValue ::= '"' (\[^%&"\] \| PEReference \| Reference)\* '"'

      \| "'" (\[^%&'\] \| PEReference \| Reference)\* "'"

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### NotationDecl

          static final int NotationDecl

      NotationDecl ::= '\<' '!NOTATION' S Name S (ExternalID \| PublicID) S? '\>'

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ExternalID

          static final int ExternalID

      ExternalID ::= 'SYSTEM' S SystemLiteral

      \| 'PUBLIC' S PubidLiteral S SystemLiteral

      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### token

          void token(int token,
                     java.lang.String value)

      The interface call-back method. Receives an XML token and it's corresponding value
      Parameters:
      `token` - The XML token constant as specified in the interface.

      `value` - The corresponding substring from the parsed text.

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

- **[Prev Class](XMLText.md)**
- **[Next Class](XMLTokenizer.md)**

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

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
