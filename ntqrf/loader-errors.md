Review loader errors.

OSD-04300
Unable to read complete record from the datafile

Cause: Datafile ended in the middle of a record. This error occurs when loading files with a fixed record length.

Action: Verify that the datafile is of correct length and contains complete records.

OSD-04301
Record size too large

Cause: Specified record size is too large to load.

Action: Reduce record size and reload data.

OSD-04302
Invalid record type, load options, or both

Cause: Control file's Windows file processing options string contains an invalid option or keyword.

Action: Set Windows file processing options string to an acceptable value.

**Parent topic:** [OSD-04000 to OSD-04599: Windows-Specific Oracle Database Messages](windows-specific-oracle-database-messages.md)
