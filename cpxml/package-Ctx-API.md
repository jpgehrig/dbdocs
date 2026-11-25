The XML context-related types and interfaces are represented in the `Ctx` namespace. These include `Ctx`datatypes, `MemAllocator`methods, and `TCtx` methods.

**See Also:**

[Oracle XML Developer's Kit Programmer's Guide](../adxdk/adx_cp_unified.md)

### Ctx Datatypes

Table 2-1 summarizes the datatypes of the `Ctx` package.

Table 2-1 Summary of Datatypes; Ctx Package

| Datatype  | Description                  |
|:----------|:-----------------------------|
| encoding  | A single supported encoding. |
| encodings | An array of encodings.       |

#### encoding

A single supported encoding.

##### Definition

    typedef struct encoding {
       oratext *encname;
       oratext *encvalue;
    } encoding;

#### encodings

An array of encodings.

##### Definition

    typedef struct encodings {
       unsigned num;
       encoding *enc;
    } encodings;

### MemAllocator Interface

Table 2-2 summarizes the methods available through the `MemAllocator` interface.

Table 2-2 Summary of MemAllocator Methods; Ctx Package

| Function        | Summary                                                            |
|:----------------|:-------------------------------------------------------------------|
| alloc()         | Allocates memory of given size.                                    |
| dealloc()       | Deallocate memory pointed to by the argument.                      |
| ~MemAllocator() | Virtual destructor - interface level handle to actual destructors. |

#### alloc()

This is a virtual member function that defines a prototype for user defined allocator functions

##### Syntax

    virtual void* alloc(
       ub4 size) = 0;

| Parameter | Description |
|:----------|:------------|
| `size`    | memory size |

#### dealloc()

This is a virtual member function that defines a prototype for user defined deallocator functions. Such deallocators are supposed to deallocate memory allocated by the alloc member functions

##### Syntax

    virtual void dealloc(
       void* ptr) = 0;

| Parameter | Description                            |
|:----------|:---------------------------------------|
| `ptr`     | pointer to previously allocated memory |

#### ~MemAllocator()

It provides an interface level handle to actual destructors that can be invoked without knowing their names or implementations

##### Syntax

    virtual ~MemAllocator() {}

### TCtx Interface

Table 2-3 summarizes the methods available through the `TCtx` interface.

Table 2-3 Summary of TCtx Methods; Ctx Package

| Function          | Summary                                                    |
|:------------------|:-----------------------------------------------------------|
| TCtx()            | Class constructor.                                         |
| getEncoding()     | Get data encoding in use by XML context.                   |
| getErrHandler()   | Get Error Handler provided by the user.                    |
| getMemAllocator() | Get memory allocator.                                      |
| isSimple()        | Get a flag that indicates if data encoding is simple.      |
| isUnicode()       | Get a flag indicating if data encoding is Unicode.         |
| ~TCtx()           | Destructor - clears space and destroys the implementation. |

#### TCtx()

TCtx constructor. It throws `XmlException` if it fails to create a context object.

| Syntax                                                                                                                                                                                 | Description                                                                                                                                                                       |
|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `TCtx() throw (XMLException)`                                                                                                                                                          | This constructor creates the context object and initializes it with default values of parameters.                                                                                 |
| `TCtx(`<br>`   oratext* name,`<br>`   ErrorHandler* errh = NULL,`<br>`   MemAllocator* memalloc = NULL,`<br>`   encodings* encs = NULL)`<br>`throw (XMLException)`                     | This constructor creates the context object and initializes it with parameter values provided by the user.                                                                        |
| `TCtx(`<br>`   oratext* name,`<br>`   up4 inpblksize,`<br>`   ErrorIfs* errh = NULL,`<br>`   MemAllocator* memalloc = NULL,`<br>`   encodings* encs = NULL)`<br>`throw (XMLException)` | This constructor creates the context object and initializes it with parameter values provided by the user. Takes an additional parameter for memory block size from input source. |

| Parameter    | Description                        |
|:-------------|:-----------------------------------|
| `name`       | user defined name of the context   |
| `errh`       | user defined error handler         |
| `memalloc`   | user defined memory allocator      |
| `encs`       | user specified encodings           |
| `inpblksize` | memory block size for input source |

##### Returns

`(TCtx)` Context object

#### getEncoding()

Returns data encoding in use by XML context. Ordinarily, the data encoding is chosen by the user, so this function is not needed. However, if the data encoding is not specified, and allowed to default, this function can be used to return the name of that default encoding.

##### Syntax

    oratext* getEncoding() const;

##### Returns

`(oratext *)` name of data encoding

#### getErrHandler()

This member functions returns Error Handler provided by the user when the context was created, or `NULL` if none were provided.

##### Syntax

    ErrorHandler* getErrHandler() const;

##### Returns

`(ErrorHandler *)` Pointer to the Error Handler object, or `NULL`

#### getMemAllocator()

This member function returns memory allocator provided by the user when the context was created, or default memory allocator. It is important that this memory allocator is used for all C level memory allocations

##### Syntax

    MemAllocator* getMemAllocator() const;

##### Returns

`(MemAllocator*)` Pointer to the memory allocator object

#### isSimple()

Returns a flag saying whether the context's data encoding is "simple", single-byte for each character, like ASCII or EBCDIC.

##### Syntax

    boolean isSimple() const;

##### Returns

`(boolean)` `TRUE` of data encoding is "simple", `FALSE` otherwise

#### isUnicode()

Returns a flag saying whether the context's data encoding is Unicode, UTF-16, with two-byte for each character.

##### Syntax

    boolean isUnicode() const;

##### Returns

`(boolean)` `TRUE` if data encoding is Unicode, `FALSE` otherwise

#### ~TCtx()

Destructor - should be called by the user the context object is no longer needed

##### Syntax

    ~Tctx();
