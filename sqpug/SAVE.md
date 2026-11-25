## 12.39 SAVE

### Syntax

    SAV[E] [FILE] file_name[.ext] [CRE[ATE] | REP[LACE] | APP[END]]

Saves the contents of the SQL buffer in an operating system script.

### Terms

    FILE

Keyword to specify that the following argument is the name you want to give to the saved script. This optional keyword is usually omitted.

If you want to save the script with the name file, because it is a command keyword, you need to put the name file in single quotes.

    file_name[.ext]

Specifies the script in which you wish to save the buffer's contents.

    CREATE

Creates a new file with the name specified. This is the default behavior.

    REP[LACE]

Replaces the contents of an existing file. If the file does not exist, REPLACE creates the file.

    APP[END]

Adds the contents of the buffer to the end of the file you specify.

### Usage

If you do not specify an extension, SQL\*Plus assumes the default command-file extension (normally SQL). See [SET SUF\[FIX\] {SQL \| text}](SET-system-variable-summary.md) for information on changing this default extension.

If you wish to SAVE a file under a name identical to a SAVE command clause (CREATE, REPLACE, or APPEND), you must specify a file extension.

When you SAVE the contents of the SQL buffer, SAVE adds a line containing a slash (/) to the end of the file.

### Examples

To save the contents of the buffer in a file named DEPTSALRPT with the extension SQL, enter

    SAVE DEPTSALRPT

To save the contents of the buffer in a file named DEPTSALRPT with the extension OLD, enter

    SAVE DEPTSALRPT.OLD
