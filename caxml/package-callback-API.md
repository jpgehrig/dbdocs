The Callback package defines macros that declare functions (or function pointers) for XML callbacks. Callbacks are used for error-message handling, memory allocation and freeing, and stream operations.

The following table summarizes the methods available through the Callback interface.

Table 2-1 Summary of Callback Methods for XML C Implementation

| Function             | Summary                                    |
|:---------------------|:-------------------------------------------|
| XML_ACCESS_CLOSE_F() | User-defined access method close callback. |
| XML_ACCESS_OPEN_F()  | User-defined access method open callback.  |
| XML_ACCESS_READ_F()  | User-defined access method read callback.  |
| XML_ALLOC_F()        | Low-level memory allocation.               |
| XML_ERRMSG_F()       | Handles error message.                     |
| XML_FREE_F()         | Low-level memory freeing.                  |
| XML_STREAM_CLOSE_F() | User-defined stream close callback.        |
| XML_STREAM_OPEN_F()  | User-defined stream open callback.         |
| XML_STREAM_READ_F()  | User-defined stream read callback.         |
| XML_STREAM_WRITE_F() | User-defined stream write callback.        |

### XML_ACCESS_CLOSE_F()

This macro defines a prototype for the close function callback used to access a URL.

### XML_ACCESS_OPEN_F()

This macro defines a prototype for the open function callback used to access a URL.

### XML_ACCESS_READ_F()

This macro defines a prototype for the read function callback used to access a URL.

### XML_ALLOC_F()

This macro defines a prototype for the low-level memory `alloc` function provided by the user. If no allocator is provided, `malloc` is used. Memory should not be zeroed by this function. Matches XML_FREE_F().

### XML_ERRMSG_F()

This macro defines a prototype for the error message handling function. If no error message callback is provided at XML initialization time, errors will be printed to `stderr`. If a handler is provided, it will be invoked instead of printing to stderr.

### XML_FREE_F()

This macro defines a prototype for the low-level memory free function provided by the user. If no allocator is provided, free() is used. Matches XML_ALLOC_F().

### XML_STREAM_CLOSE_F()

This macro defines a prototype for the close function callback, called to close an open source and free its resources.

### XML_STREAM_OPEN_F()

This macro defines a prototype for the open function callback, which is called once to open the input source. This function should return `XMLERR_OK` on success.

### XML_STREAM_READ_F()

This macro defines a prototype for the read function callback, called to read data from an open source into a buffer, returning the number of bytes read (\< `0` on error). The `eoi` flag determines if this is the final block of data.

On EOI, the close function will be called automatically.

#### Syntax

    #define XML_STREAM_READ_F(func, xctx, sctx, path, dest, size, nraw, eoi)
    xmlerr func(
       xmlctx *xctx,
       void *sctx,
       oratext *path,
       oratext *dest,
       size_t size,
       sbig_ora *nraw,
       boolean *eoi);

| Parameter | In/Out  | Description                                      |
|:----------|:--------|:-------------------------------------------------|
| `xctx`    | `IN`    | XML context                                      |
| `sctx`    | `IN`    | user-defined stream context                      |
| `path`    | `IN`    | full URI of the open source (for error messages) |
| `dest`    | `(OUT)` | destination buffer to read data into             |
| `size`    | `IN`    | size of destination buffer                       |
| `nraw`    | `(OUT)` | number of bytes read                             |
| `eoi`     | `(OUT)` | signal to end of information; last chunk         |

#### Returns

`(xmlerr)` numeric error code, `0` on success

**See Also:**

XML_STREAM_OPEN_F(), XML_STREAM_CLOSE_F(), XML_STREAM_WRITE_F()

### XML_STREAM_WRITE_F()

This macro defines a prototype for the write function callback, called to write data to a user-defined stream.

#### Syntax

    #define XML_STREAM_WRITE_F(func, xctx, sctx, path, src, size)
    xmlerr func(
       xmlctx *xctx,
       void *sctx,
       oratext *path,
       oratext *src,
       size_t size);

| Parameter | In/Out | Description                                      |
|:----------|:-------|:-------------------------------------------------|
| `xctx`    | `IN`   | XML context                                      |
| `sctx`    | `IN`   | user-defined stream context                      |
| `path`    | `IN`   | full URI of the open source (for error messages) |
| `src`     | `IN`   | source buffer to read data from                  |
| `size`    | `IN`   | size of source in bytes                          |

#### Returns

`(xmlerr)` numeric error code, `0` on success

**See Also:**

XML_STREAM_OPEN_F(), XML_STREAM_CLOSE_F(), XML_STREAM_READ_F()
