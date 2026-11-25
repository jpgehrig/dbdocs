Methods of the `Bytes` class enable you to perform specific tasks related to `Bytes` objects.

Table 13-9 Summary of Bytes Methods

| Method      | Summary                                                           |
|:------------|:------------------------------------------------------------------|
| Bytes()     | `Bytes` class constructor.                                        |
| byteAt()    | Returns the byte at the specified position of the `Bytes` object. |
| getBytes()  | Returns a byte array from the `Bytes` object.                     |
| isNull()    | Tests whether the `Bytes` object is `NULL`.                       |
| length()    | Returns the number of bytes in the `Bytes` object.                |
| operator=() | Assignment operator for `Bytes` class.                            |
| setNull()   | Sets the `Bytes` object to `NULL`.                                |

### 13.8.1 Bytes()

`Bytes` class constructor.

| Syntax                                                                                                                                     | Description                                                                        |
|:-------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------|
| `Bytes(`<br>`   Environment *env = NULL);`                                                                                                 | Creates a `Bytes` object.                                                          |
| `Bytes(`<br>`   unsigned char *value,`<br>`   unsigned int count`<br>`   unsigned int offset = 0,`<br>`   const Environment *env = NULL);` | Creates a `Bytes` object that contains a subarray of bytes from a character array. |
| `Bytes(`<br>`   const Bytes &e);`                                                                                                          | Creates a copy of a `Bytes` object, use the syntax                                 |

| Parameter | Description                                                                            |
|:----------|:---------------------------------------------------------------------------------------|
| `env`     | Environment                                                                            |
| `value`   | Initial value of the new object                                                        |
| `count`   | The size of the subset of the character array that is copied into the new bytes object |
| `offset`  | The first position from which to begin copying the character array                     |
| `e`       | The source `Bytes` object.                                                             |

### 13.8.2 byteAt()

Returns the byte at the specified position in the `Bytes` object.

#### Syntax

    unsigned char byteAt(
       unsigned int index) const;

| Parameter | Description                                                                                                    |
|:----------|:---------------------------------------------------------------------------------------------------------------|
| `index`   | The position of the byte to be returned from the `Bytes` object; the first byte of the `Bytes` object is at 0. |

### 13.8.3 getBytes()

Copies bytes from a `Bytes` object into the specified byte array.

#### Syntax

    void getBytes(
       unsigned char *dst,
       unsigned int count,
       unsigned int srcBegin = 0,
       unsigned int dstBegin = 0) const;

| Parameter  | Description                                                                                                                              |
|:-----------|:-----------------------------------------------------------------------------------------------------------------------------------------|
| `dst`      | The destination buffer into which data from the `Bytes` object is to be written.                                                         |
| `count`    | The number of bytes to copy.                                                                                                             |
| `srcBegin` | The starting position at which data is to be read from the `Bytes` object; the position of the first byte in the `Bytes` object is at 0. |
| `dstBegin` | The starting position at which data is to be written in the destination buffer; the position of the first byte in `dst` is at 0.         |

### 13.8.4 isNull()

Tests whether the `Bytes` object is atomically `NULL`. If the `Bytes` object is atomically `NULL`, then `TRUE` is returned; otherwise `FALSE` is returned.

#### Syntax

    bool isNull() const;

### 13.8.5 length()

This method returns the length of the `Bytes` object.

#### Syntax

    unsigned int length() const;

### 13.8.6 operator=()

Assignment operator for `Bytes` class.

#### Syntax

    void operator=(
       const Bytes& bytes);

| Parameter | Description           |
|:----------|:----------------------|
| `bytes`   | The original `Bytes`. |

### 13.8.7 setNull()

This method sets the `Bytes` object to atomically `NULL`.

#### Syntax

    void setNull();
