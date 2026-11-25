Package `UTL_FILE` allows your PL/SQL programs to read and write the operating system text files.

It provides a restricted version of the standard operating system stream file I/O, including open, put, get, and close operations. When you want to read or write a text file, you call the function `fopen`, which returns a file handle for use in subsequent procedure calls. For example, the procedure `put_line` writes a text string and line terminator to an open file, and the procedure `get_line` reads a line of text from an open file into an output buffer.

`FSEEK`, a `UTL_FILE` subprogram, adjusts the file pointer forward or backward within the file by the number of bytes specified. In order for `UTL_FILE.FSEEK` to work correctly, the lines in the file must have the platform-specific line terminator characters. On Windows platform, the correct line terminator characters are `<CR><LF>`.

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/UTL_FILE.md) for more information about `UTL_FILE`

- [Oracle Database Development Guide](../adfns/web-applications.md) for information about "Retrieving HTTP URL Contents from PL/SQL"

**Parent topic:** [Developing Applications for Windows](developing-applications-for-windows.md)
