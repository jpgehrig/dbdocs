Lists and describes OCI messaging functions.

The user message API provides a simple interface for cartridge developers to retrieve their own messages and Oracle Database messages.

**See Also:**

[Oracle Database Data Cartridge Developer's Guide](../addci/roadmap-to-building-a-data-cartridge.md)

Table 31-7 lists the OCI messaging functions that are described in this section.

Table 31-7 OCI Messaging Functions

| Function          | Purpose                                                                                             |
|:------------------|:----------------------------------------------------------------------------------------------------|
| OCIMessageClose() | Close a message handle and free any memory associated with the handle                               |
| OCIMessageGet()   | Retrieve a message. If the buffer is not zero, then the function copies the message into the buffer |
| OCIMessageOpen()  | Open a message handle in a specified language                                                       |

### 31.7.1 OCIMessageClose()

Closes a message handle and frees any memory associated with this handle.

#### Purpose

Closes a message handle and frees any memory associated with this handle.

#### Syntax

    sword OCIMessageClose ( void      *hndl,
                            OCIError  *errhp,
                            OCIMsg    *msgh );

#### Parameters

hndl (IN/OUT)
Pointer to an OCI environment or user session handle for the message language.

errhp (IN/OUT)
The OCI error handle. If there is an error, then it is recorded in `errhp`, and the function returns a `NULL` pointer. Diagnostic information can be obtained by calling `OCIErrorGet()`.

msgh (IN/OUT)
A pointer to a message handle that was previously opened by `OCIMessageOpen()`.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`.

**Related Topics**

- OCIMessageOpen()
- [OCIErrorGet()](miscellaneous-functions.md)

### 31.7.2 OCIMessageGet()

Gets a message with the given message number.

#### Purpose

Gets a message with the given message number.

#### Syntax

    OraText *OCIMessageGet ( OCIMsg      *msgh,
                             ub4          msgno,
                             OraText     *msgbuf,
                             size_t       buflen );

#### Parameters

msgh (IN/OUT)
Pointer to a message handle that was previously opened by `OCIMessageOpen()`.

msgno (IN)
The message number.

msgbuf (OUT)
Pointer to a destination buffer for the retrieved message. If `buflen` is zero, then it can be a `NULL` pointer.

buflen (IN)
The size of the destination buffer.

#### Comments

If `buflen` is not zero, then the function copies the message into the buffer pointed to by `msgbuf`. If `buflen` is zero, then the message is copied into a message buffer inside the message handle pointed to by `msgh`.

#### Returns

It returns the pointer to the `NULL`-terminated message string. If the translated message cannot be found, then it tries to return the equivalent English message. If the equivalent English message cannot be found, then it returns a `NULL` pointer.

**Related Topics**

- OCIMessageOpen()

### 31.7.3 OCIMessageOpen()

Opens a message-handling facility in a specified language.

#### Purpose

Opens a message-handling facility in a specified language.

#### Syntax

    sword OCIMessageOpen ( void             *hndl,
                           OCIError         *errhp,
                           OCIMsg           *msghp,
                           const OraText    *product,
                           const OraText    *facility,
                           OCIDuration       dur );

#### Parameters

hndl (IN/OUT)
Pointer to an OCI environment or user session handle for the message language.

errhp (IN/OUT)
The OCI error handle. If there is an error, then it is recorded in `errhp`, and the function returns a `NULL` pointer. Diagnostic information can be obtained by calling `OCIErrorGet()`.

msghp (OUT)
A message handle for return.

product (IN)
A pointer to a product name. The product name is used to locate the directory for messages. Its location depends on the operating system. For example, in Solaris, the directory of message files for the `rdbms` product is `$ORACLE_HOME/rdbms`.

facility (IN)
A pointer to a facility name in the product. It is used to construct a message file name. A message file name follows the conversion with `facility` as prefix. For example, the message file name for the `img` facility in the American language is `imgus.msb`, where `us` is the abbreviation for the American language and `msb` is the message binary file extension.

dur (IN)
The duration for memory allocation for the return message handle. It can have the following values:

- `OCI_DURATION_PROCESS`

- `OCI_DURATION_SESSION`

- `OCI_DURATION_STATEMENT`

#### Comments

`OCIMessageOpen()` first tries to open the message file corresponding to `hndl`. If it succeeds, then it uses that file to initialize a message handle. If it cannot find the message file that corresponds to the language, then it looks for a primary language file as a fallback. For example, if the Latin American Spanish file is not found, then it tries to open the Spanish file. If the fallback fails, then it uses the default message file, whose language is `AMERICAN`. The function returns a pointer to a message handle into the `msghp` parameter.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)
