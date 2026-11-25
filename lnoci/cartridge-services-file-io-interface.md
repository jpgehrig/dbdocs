Lists and describes cartridge services file I/O interface functions.

Table 29-5 lists the file I/O interface functions that are described in this section.

Table 29-5 File I/O Interface Functions

| Function           | Purpose                               |
|:-------------------|:--------------------------------------|
| OCIFileClose()     | Close a previously opened file        |
| OCIFileExists()    | Test to see if the file exists        |
| OCIFileFlush()     | Write buffered data to a file         |
| OCIFileGetLength() | Get the length of a file              |
| OCIFileInit()      | Initialize the OCIFile package        |
| OCIFileOpen()      | Open a file                           |
| OCIFileRead()      | Read from a file into a buffer        |
| OCIFileSeek()      | Change the current position in a file |
| OCIFileTerm()      | Terminate the OCIFile package         |
| OCIFileWrite()     | Write `buflen` bytes into the file    |

**See Also:**

[Oracle Database Data Cartridge Developer's Guide](../addci/using-cartridge-services.md) for more information about using these functions

### OCIFileObject

The `OCIFileObject` data structure holds information about the way in which a file should be opened and the way in which it is accessed after it has been opened. When this structure is initialized by `OCIFileOpen()`, it becomes an identifier through which operations can be performed on that file. It is a necessary parameter to every function that operates on open files. This data structure is opaque to OCIFile clients. It is initialized by OCIFileOpen() and terminated by OCIFileClose().

### 29.6.1 OCIFileClose()

Closes a previously opened file.

#### Purpose

Closes a previously opened file.

#### Syntax

    sword OCIFileClose( void          *hndl,
                        OCIError      *err,
                        OCIFileObject *filep );

#### Parameters

hndl (IN)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

filep (IN/OUT)
A pointer to a file identifier to be closed.

#### Comments

Once this function returns OCI_SUCCESS, the `OCIFileObject` structure pointed to by `filep` is destroyed. Therefore, you should not attempt to access this structure after this function returns OCI_SUCCESS.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 29.6.2 OCIFileExists()

Tests to see if the file exists.

#### Purpose

Tests to see if the file exists.

#### Syntax

    sword OCIFileExists( void     *hndl,
                         OCIError *err,
                         OraText  *filename,
                         OraText  *path,
                         ub1      *flag );

#### Parameters

hndl (IN)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

filename (IN)
The file name as a `NULL`-terminated string.

path (IN)
The path of the file as a `NULL`-terminated string.

flag (OUT)
Set to `TRUE` if the file exists or `FALSE` if it does not.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 29.6.3 OCIFileFlush()

Writes buffered data to a file.

#### Purpose

Writes buffered data to a file.

#### Syntax

    sword OCIFileFlush( void          *hndl
                        OCIError      *err,
                        OCIFileObject *filep );

#### Parameters

hndl (IN)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

filep (IN/OUT)
A file identifier that uniquely references the file.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 29.6.4 OCIFileGetLength()

Gets the length of a file.

#### Purpose

Gets the length of a file.

#### Syntax

    sword OCIFileGetLength( void     *hndl,
                            OCIError *err,
                            OraText  *filename,
                            OraText  *path,
                            ubig_ora *lenp );

#### Parameters

hndl (IN)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

filename (IN)
The file name as a `NULL`-terminated string.

path (IN)
The path of the file as a `NULL`-terminated string.

lenp (OUT)
Set to the length of the file in bytes.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 29.6.5 OCIFileInit()

Initializes the OCIFile package.

#### Purpose

This function must be called before any other OCIFile routine is called.

#### Syntax

    sword OCIFileInit( void     *hndl,
                       OCIError *err );

#### Parameters

hndl (IN)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 29.6.6 OCIFileOpen()

Opens a file.

#### Purpose

Opens a file.

#### Syntax

    sword OCIFileOpen( void            *hndl,
                       OCIError        *err,
                       OCIFileObject  **filep,
                       OraText         *filename,
                       OraText         *path,
                       ub4              mode,
                       ub4              create,
                       ub4              type );

#### Parameters

hndl (IN)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

filep (IN/OUT)
The file identifier.

filename (IN)
The file name as a `NULL`-terminated string.

path (IN)
The path of the file as a `NULL`-terminated string.

mode (IN)
The mode in which to open the file. Valid modes are

`OCI_FILE_READ_ONLY`

`OCI_FILE_WRITE_ONLY`

`OCI_FILE_READ_WRITE`

create (IN)
Indicates if the file is to be created if it does not exist. Valid values are:

`OCI_FILE_TRUNCATE` — Create a file regardless of whether it exists. If the file exists, overwrite the existing file.

`OCI_FILE_EXCL` — Fail if the file exists; otherwise, create a file.

`OCI_FILE_CREATE` — Open the file if it exists, and create it if it does not.

`OCI_FILE_APPEND` — Set the file pointer to the end of the file prior to writing. This flag can be used with the logical operator OR with `OCI_FILE_CREATE`.

type (IN)
File type. Valid values are:

`OCI_FILE_TEXT`

`OCI_FILE_BIN`

`OCI_FILE_STDIN`

`OCI_FILE_STDOUT`

`OCI_FILE_STDERR`

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 29.6.7 OCIFileRead()

Reads from a file into a buffer.

#### Purpose

Reads from a file into a buffer.

#### Syntax

    sword OCIFileRead( void          *hndl,
                       OCIError      *err,
                       OCIFileObject *filep,
                       void          *bufp,
                       ub4            bufl,
                       ub4           *bytesread );

#### Parameters

hndl (IN)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

filep (IN/OUT)
A file identifier that uniquely references the file.

bufp (IN)
The pointer to a buffer into which the data is read. The length of the allocated memory is assumed to be `bufl`.

bufl (IN)
The length of the buffer in bytes.

bytesread (OUT)
The number of bytes read.

#### Comments

As many bytes as possible are read into the user buffer. The read ends either when the user buffer is full, or when it reaches end-of-file.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 29.6.8 OCIFileSeek()

Changes the current position in a file.

#### Purpose

Changes the current position in a file.

#### Syntax

    sword OCIFileSeek( void          *hndl,
                       OCIError      *err,
                       OCIFileObject *filep,
                       uword          origin,
                       ubig_ora       offset,
                       sb1            dir );

#### Parameters

hndl (IN)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

filep (IN/OUT)
A file identifier that uniquely references the file.

origin(IN)
The starting point from which to seek. Use one of the following values:

`OCI_FILE_SEEK_BEGINNING` (beginning)

`OCI_FILE_SEEK_CURRENT` (current position)

`OCI_FILE_SEEK_END` (end of file)

offset (IN)
The number of bytes from the origin where reading begins.

dir (IN)
The direction to go from the origin.

**Note:**

The direction can be either `OCIFILE_FORWARD` or `OCIFILE_BACKWARD`.

#### Comments

This function allows a seek past the end of the file. Reading from such a position causes an end-of-file condition to be reported. Writing to such a position does not work on all file systems. This is because some systems do not allow files to grow dynamically. They require that files be preallocated with a fixed size. Note that this function performs a seek to a byte location.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 29.6.9 OCIFileTerm()

Terminates the OCIFile package.

#### Purpose

This function must be called after the OCIFile package is no longer being used.

#### Syntax

    sword OCIFileTerm( void     *hndl,
                       OCIError *err );

#### Parameters

hndl (IN)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 29.6.10 OCIFileWrite()

Writes` buflen` bytes into the file.

#### Purpose

Writes` buflen` bytes into the file.

#### Syntax

    sword OCIFileWrite( void          *hndl,
                        OCIError      *err,
                        OCIFileObject *filep,
                        void          *bufp,
                        ub4            buflen,
                        ub4           *byteswritten );

#### Parameters

hndl (IN)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

filep (IN/OUT)
A file identifier that uniquely references the file.

bufp(IN)
The pointer to a buffer from which the data is written. The length of the allocated memory is assumed to be `buflen`.

buflen (IN)
The length of the buffer in bytes.

byteswritten (OUT)
The number of bytes written.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)
