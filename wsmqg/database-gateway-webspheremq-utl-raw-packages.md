Use the Oracle Visual Workbench for developing applications that access WebSphere MQ through the gateway. The Oracle Visual Workbench defines an interface for accessing WebSphere MQ and automatically generates the PL/SQL code (the MIP) for Oracle applications to interface with the gateway. Refer to the Oracle Procedural Gateway Visual Workbench for WebSphere MQ Installation and User's Guide for Microsoft Windows (32-Bit) for more information about Oracle Visual Workbench.

### Message Data Types

Messages sent to a WebSphere MQ queue or retrieved from a WebSphere MQ queue are transferred as untyped data by the MIP procedures.

When data profiles are defined in the MIP, the MIP converts message data from Oracle data types to target data types that the receiving application understands. The message data is packed into a buffer of the `RAW` data type before being sent to the WebSphere MQ queue. The same conversion process applies when receiving a message. The MIP unpacks the message from the buffer and converts it to specified Oracle data types.

The MIP uses the functions of the `UTL_RAW` package to perform the message data conversions. The `UTL_RAW` package is a PL/SQL package that contains procedures for converting and packing message data which is sent back and forth through the WebSphere MQ queues using the `RAW` data type and PL/SQL data types.

When necessary, you can enhance the message data conversions in the generated MIP with the `UTL_RAW` functions. When no data profiles are defined in the MIP, you can create your own data conversion procedures with `UTL_RAW` functions, calling these functions before sending a message and immediately after receiving a message.

The `UTL_RAW` package is not included with the gateway. It is shipped with each Oracle database. Refer to your Oracle DBA for information about installing the `UTL_RAW` package.

### UTL_RAW Functions

This topic describes the `UTL_RAW` functions.

The `UTL_RAW` functions are called with the following syntax:

    UTL_RAW.function(arg1, arg2, ...)

The function name, arguments, their Oracle data types, and the return value data type are provided with each function description in this appendix. For ease of description, the functions are described with PL/SQL syntax that shows the resulting function value placed in a variable as follows:

    result := UTL_RAW.function(arg1, arg2, ...);

However, the function can also be used as a component in a PL/SQL expression. For example, the function takes two characters strings, Hello and world!, converts them to raw message data with `UTL_RAW`.`CAST_TO_RAW`, concatenates them with `UTL_RAW`.`CONCAT`, and uses the gateway to send them to a WebSphere MQ queue. The same message is retrieved from the queue, converted to a character data type with `UTL_RAW.CAST_TO_VARCHAR2`, and then printed.

#### UTL_RAW.TO_RAW

`PGM_UTL.TO_RAW` converts values of the `PGM.MQOD`, `PGM.MQMD`, `PGM.MQPMO` and `PGM.MQGMO` object to into raw values.

##### Syntax

    result := PGM_UTL.TO_RAW(input);

where:

- result is a variable that holds the output value of the function. It is of the RAW data type.

- input is the input value of the `PGM`.`MQOD`, `PGM`.`MQMD`, `PGM`.`MQPMO` or `PGM`.`MQGMO` data type objects that is converted to raw data.

#### UTL_RAW.BIT_AND

`UTL_RAW.BIT_AND` performs a bitwise logical `AND` operation on two raw values. If the values have different lengths, then the `AND` operation is terminated after the last byte of the shorter of the two values. The unprocessed portion of the longer value is appended to the partial result to produce the final result. The length of the resulting value equals the longer of the two input values.

##### Syntax

    result := UTL_RAW.BIT_AND(input1, input2);

where:

- result is the variable that holds the output value of the function. It is data type RAW. The value is null if `input1` or `input2` is null.

- input1 is an input value of data type `RAW` to `BIT_AND` with `input2`.

- input2 is an input value of data type `RAW` to `BIT_AND` with `input1`.

#### UTL_RAW.BIT_COMPLEMENT

`UTL_RAW`.`BIT_COMPLEMENT` performs a bitwise logical `COMPLEMENT` operation of a raw value. The length of the resulting value equals the length of the input value.

##### Syntax

    result := UTL_RAW.BIT_COMPLEMENT(input);

where:

- `result` is the variable that holds the output value of the function. It is of `RAW` data type. The value is null if `input` is null.

- `input` is an input value of the `RAW` data type on which to perform the `COMPLEMENT` operation.

#### UTL_RAW.BIT_OR

`UTL_RAW.BIT_OR` performs a bitwise logical `OR` operation of two raw values. If the values have different lengths, then the `OR` operation is terminated after the last byte of the shorter of the two values. The unprocessed portion of the longer value is appended to the partial result to produce the final result. The length of the resulting value equals the length of the longer of the two input values.

##### Syntax

    result := UTL_RAW.BIT_OR(input1, input2);

where:

- `result` is the variable that holds the output value of the function. It is of the data type `RAW`. The value is null if `input1` or `input2` is null.

- `input1` is an input value of the `RAW` data type to `BIT_OR` with `input2`.

- `input2` is an input value of the `RAW` data type to `BIT_OR` with `input1`.

#### UTL_RAW.BIT_XOR

`UTL_RAW`.`BIT_XOR` performs a bitwise logical `EXCLUSIVE` `OR` operation of two raw values. If the values have different lengths, then the `EXCLUSIVE` `OR` operation is terminated after the last byte of the shorter of the two values. The unprocessed portion of the longer value is appended to the partial result to produce the final result. The length of the resulting value equals the longer of the two input values.

##### Syntax

    result := UTL_RAW.BIT_XOR(input1, input2);

where:

- `result` is the variable that holds the output value of the function. It is data type `RAW`. The value is null if `input1` or `input2` is null.

- `input1` is an input value of the `RAW` data type to `EXCLUSIVE` `OR` with `input2`.

- `input2` is an input value of the `RAW` data type to `EXCLUSIVE` `OR` with `input1`.

#### UTL_RAW.CAST_TO_RAW

`UTL_RAW`.`CAST_TO_RAW` converts a value of data type `VARCHAR2` into a raw value with the same number of bytes. The input value is treated as if it were composed of single 8-bit bytes, not characters. Multibyte character boundaries are ignored. The data is not modified in any way, it is only changed to data type `RAW`.

##### Syntax

    result := UTL_RAW.CAST_TO_RAW(input);

where:

- `result` is the variable that holds the output value of the function. It is data type `RAW`. The value is null if `input` is null.

- `input` is the input value of the `VARCHAR2` data type to convert to raw data.

#### UTL_RAW.CAST_TO_VARCHAR2

`UTL_RAW`.`CAST_TO_VARCHAR2` converts a raw value into a value of data type `VARCHAR2` with the same number of data bytes. The result is treated as if it were composed of single 8-bit bytes, not characters. Multibyte character boundaries are ignored. The data is not modified in any way, it is only changed to data type `VARCHAR2`.

##### Syntax

    result := UTL_RAW.CAST_TO_VARCHAR2(input);

where:

- `result` is the variable that holds the output value of the function. It is data type `VARCHAR2`. The value is null if `input` is null.

- `input` is the input value of the `RAW` data type to convert to data type `VARCHAR2`.

#### UTL_RAW.COMPARE

`UTL_RAW`.`COMPARE` compares one raw value to another raw value. If they are identical, then `UTL_RAW`.`COMPARE` returns 0. If they are not identical, then `COMPARE` returns the position of the first byte that does not match. If the input values have different lengths, then the shorter input value is padded on the right by a value that you specify.

##### Syntax

    result := UTL_RAW.COMPARE(input1, input2[, pad]);

where:

- `result` is the variable that holds the output value of the function. It is of data type `NUMBER`. A value of 0 is returned if the values of `input1` and `input2` are null or identical or the position, numbered from 1, of the first mismatched byte.

- `input1` is the first input value of the `RAW` data type to compare.

- `input2` is the second input value of the `RAW` data type to compare.

- `padis` a single byte value used to pad the shorter input value. The default is X'00'.

#### UTL_RAW.CONCAT

`UTL_RAW`.`CONCAT` concatenates a set of up to 12 raw values into a single raw value.  The values are appended together, left to right, in the order that they appear in the parameter list. Null input values are skipped, and the concatenation continues with the next non-null value.

If the sum of the lengths of the input values exceeds 32 767 bytes, then a `VALUE_ERROR` exception is raised.

##### Syntax

    result := UTL_RAW.CONCAT(input1, ...  input12);

where:

- `result` is the variable that holds the output value of the function. It is data type `RAW`. 

- `input1` `...``  input12` are the input values of `RAW` data type to concatenate.

#### UTL_RAW.CONVERT

`UTL_RAW`.`CONVERT` converts a raw value to a different character set `A` `VALUE_ERROR` exception is raised for any of the following conditions:

- The input value is null or 0 in length

- One or both of the specified character sets is missing, null, or 0 in length

- The character set names are invalid or unsupported by the Oracle database

##### Syntax

    result := UTL_RAW.CONVERT(input, new_charset, old_charset);

where:

- `result` is the variable that holds the output value of the function. It is of the `RAW` data type.

- `input` is the input value of the `RAW` data type to convert.

- `new_charset` is the Globalization Support character set to convert `input` to.

- `old_charset` is the Globalization Support character set that input is currently using.

#### UTL_RAW.COPIES

`UTL_RAW`.`COPIES` returns one or more copies of a value. The values are concatenated together. `A` `VALUE_ERROR` exception is raised for any of the following conditions:

- The input value is null or has a length of 0

- A negative number of copies is specified

- The length of the result exceeds 32 767 bytes

##### Syntax

    result := UTL_RAW.COPIES(input, number);

where:

- `result` is the variable that holds the output value of the function. It is of the `RAW` data type.

- `input` is a value of the `RAW` data type to copy.

- `number` is the number of times to copy input. It must be a positive value.

#### UTL_RAW.LENGTH

`UTL_RAW`.`LENGTH` returns the length, in bytes, of a raw value.

##### Syntax

    result := UTL_RAW.LENGTH(input);

where:

- `result` is the output value of the function. It is of the `NUMBER` data type.

- `input` is the input value of the RAW data type to evaluate.

#### UTL_RAW.OVERLAY

`UTL_RAW`.`OVERLAY` replaces a portion of a raw value with a new string of raw data.  If the new data is shorter than the length of the overlay area, then the new data is padded to make it long enough. If the new data is longer than the overlay area, then the extra bytes are ignored. If you specify an overlay area that exceeds the length of the input value, then the input value is extended according to the length specified. If you specify a starting position for the overlay area that exceeds the length of the input value, then the input value is padded to the position specified, and then the input value is further extended with the new data.

`A` `VALUE_ERROR` exception is raised for any of the following conditions:

- The new data used to overlay the input value is null or has a length of 0

- The portion of the input value to overlay is not defined

- The length of the portion to overlay exceeds 32 767 bytes

- The number of bytes to overlay is defined as less than 0

- The position within the input value to begin the overlay operation is defined as less than 1

##### Syntax

    result := UTL_RAW.OVERLAY(new_bytes, input, position, length, pad);

where:

- `result` is the variable that holds the output value of the function. It is of the `RAW` data type.

- `new_bytes` is the new value, a byte string of the `RAW` data type, to overlay input with. Bytes are selected from `new_bytes` beginning with the leftmost byte.

- `input` is the input value of data type `RAW` to overlay.

- `position` is the position within input, numbered from 1, at which to begin overlaying. This value must be greater than 0. The default is 1.

- `length` is the number of bytes to overlay. This must be greater than, or equal to, 0. The default is the length of `new_bytes`.

- `pad` is a single byte value used to pad when length exceeds the overlay length or when position exceeds the length of `input`. The default is X'00'.

#### UTL_RAW.REVERSE

`UTL_RAW`.`REVERSE` reverses the byte sequence of a raw value from end-to-end. For example, this function reverses X'0102F3' to X'F30201' or xyz to zyx. The length of the resulting value is the same length as the input value. `A` `VALUE_ERROR` exception is raised if the input value is null or has a length of 0.

##### Syntax

    result := UTL_RAW.REVERSE(input);

where:

- `result` is the output value of the function. It is of the `RAW` data type.

- `input` is the input value of the `RAW` data type to be reversed.

#### UTL_RAW.SUBSTR

`UTL_RAW`.`SUBSTR` removes bytes from a raw value. If you specify a positive number as the starting point for the bytes to remove, then `SUBSTR` counts from the beginning of the input value to find the first byte. If you specify a negative number, then `UTL_RAW`.`SUBSTR` counts backwards from the end of the input value to find the first byte.

`A` `VALUE_ERROR` exception is raised for any of the following conditions:

- The position to begin the removal is specified as 0

- The number of bytes to remove is specified as less than 0

##### Syntax

    result := UTL_RAW.SUBSTR(input, position[,length]);

where:

- `result` is the variable that holds the output value of the function. It is of the `RAW` data type. The value is the specified byte or bytes from `input`, or the value is a null value if `input` is null.

- `input` is the input value of the `RAW` data type from which to extract a portion of its bytes.

- `position` is the byte position from which to start extraction. This value cannot be 0. If the value of `position` is negative, then `SUBSTR` counts backwards from the end of input.

- `length` is the number of bytes to extract from `input` after `position`. This value must be greater than 0. When not specified, all bytes to the end of input are returned.

#### UTL_RAW.TRANSLATE

`UTL_RAW`.`TRANSLATE` changes the value of some of the bytes in a raw value according to a scheme that you specify. Bytes in the input value are compared to a matching string, and when found to match, the byte at the same position in the replacement string is copied to the result. It is omitted from the result if the offset exceeds the length of the replacement string. Bytes in the input value that do not appear in the matching string are copied to the resulting value. Only the leftmost occurrence of a byte in the matching string is used, and subsequent duplicate occurrences are ignored.

If the matching string contains more bytes than the replacement string, then the extra bytes at the end of the matching string have no corresponding bytes in the replacement string. Any bytes in the input value that match such bytes are omitted from the resulting value.

`A` `VALUE_ERROR` exception is raised for any of the following conditions:

- The input value is null or has a length of 0

- The matching string is null or has a length of 0

- The replacement string is null or has a length of 0

##### Syntax

    result := UTL_RAW.TRANSLATE(input, match, replace_bytes);

where:

- `result` is the variable that holds the output value of the function. It is of data type `RAW`.

- `input` is the input value of data type `RAW` to change.

- `match` specifies the byte 0codes to search for in `input` and to change to `replace_bytes`. It is of data type `RAW`.

- `replace_bytes` specifies the byte codes that replace the codes specified by match. It is of data type `RAW`.

#### UTL_RAW.TRANSLITERATE

`UTL_RAW`.`TRANSLITERATE` replaces all occurrences of any bytes in a matching string with the corresponding bytes of a replacement string. Bytes in the input value are compared to the matching string, and if they are not found, then they are copied unaltered to the resulting value. If they are found, then they are replaced in the resulting value by the byte at the same offset in the replacement string, or with the pad byte that you specify when the offset exceeds the length of the replacement string.  Only the leftmost occurrence of a byte in the matching string is used. Subsequent duplicate occurrences are ignored. The result value of `UTL_RAW`.`TRANSLITERATE` is always the same length as the input value.

If the replacement string is shorter than the matching string, then the pad byte is placed in the resulting value when a selected matching string byte has no corresponding byte in the replacement string. A VALUE_ERROR exception is raised when the input value is null or has a length of 0.

`UTL_RAW`.`TRANSLITERATE` differs from `UTL_RAW`.`TRANSLATE` in the following ways:

- Bytes in the input value that are undefined in the replacement string are padded with a value that you specify

- The resulting value is always the same length as the input value

##### Syntax

    result := UTL_RAW.TRANSLITERATE (input, replace_bytes, match, pad);

where:

- `Result` is the output value of the function. It is data type `RAW`.

- `Input` is the input value of data type `RAW` to change.

- `Replace_bytes` specifies the byte codes to which corresponding bytes of match are changed. This value can be any length that is valid for the RAW data type. The default is a null value and effectively extends with pad to the length of match as necessary.

- `Match` specifies the `byte` codes to match in `input`. The value can be any length that is valid for the RAW data type. The default is X'00' through X'FF'.

- `Pad` is a singe byte value that is used to extend the length of `replace_bytes` when `replace_bytes` is shorter than match. The default is X'00'.

  `UTL_RAW`.`TRANSLATE` differs from the `UTL_RAW`.`TRANSLITERATE` function in the following ways:

  - The raw values used for the matching and replacement strings have no default values

  - Bytes in the input value that are undefined in the replacement string are omitted in the resulting value

  - The resulting value can be shorter than the input value

#### UTL_RAW.XRANGE

`UTL_RAW`.`XRANGE` returns a raw value containing all valid one-byte codes within a range that you specify. If the starting byte value is greater than the ending byte value, then the succession of resulting bytes begin with the starting byte, wrapping from X'FF' to X'00', and end at the ending byte.

When specified, the values for the starting and ending bytes must be single-byte raw values.

##### Syntax

    result := UTL_RAW.XRANGE(start, end);

where:

- `result` is the output value of the function. It is of data type RAW.

- `start` is a single byte code to start with. The default is X'00'.

- `end` is a single byte code to end with. The default is X'FF'.
