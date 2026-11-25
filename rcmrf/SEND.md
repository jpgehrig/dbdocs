## 3.13 SEND

### Purpose

Use the `SEND` command to send a vendor-specific string to one or more channels supported by a media manager. Refer to your media management documentation to determine which commands are supported.

### Usage Notes

Unless you specify `DEVICE TYPE` or `CHANNEL`, RMAN uses all allocated channels.

On Windows platforms, use `SEND` to pass command strings to the SBT library, instead of the `ENV` parameter.

### Syntax

send::=

![Description of send.eps follows](img/send.gif)
[Description of the illustration send.eps](img_text/send.md)

([deviceSpecifier::=](deviceSpecifier.md))

### Semantics

| Syntax Element                                        | Description                                                                                                                                                                                                                                                                                                                               |
|:------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CHANNEL` `channel_id`                                | Specifies which channel to use. You must specify a case-sensitive channel ID, which is the name of the channel, after the `CHANNEL` keyword. The database uses the channel ID to report I/O errors.                                                                                                                                       |
| `DEVICE TYPE` [`deviceSpecifier`](deviceSpecifier.md) | Specifies the type of storage device and sends the command to all channels of the specified type.<br>See Also: [`deviceSpecifier`](deviceSpecifier.md)                                                                                                                                                                                    |
| `'``command``'`                                       | Specifies a vendor-specific media management command.<br>See Also: Your media management documentation to determine which commands are supported. You must only send commands supported by the media manager. The contents of the string are not interpreted by the database, but are passed unaltered to the media management subsystem. |
| `   PARMS` `'``channel_parms``'`                      | Specifies parameters for the channel communicating with the media manager.                                                                                                                                                                                                                                                                |

### Example

Example 3-56 Specifying a Tape Drive in Oracle Secure Backup

This example uses the `SEND` command to specify a tape drive for a backup of the `users` tablespace to Oracle Secure Backup. No equal sign is inserted between the parameter `OB_DEVICE` and the names of the tape drive.

    RUN
    {
      ALLOCATE CHANNEL c1 DEVICE TYPE sbt;
      SEND 'OB_DEVICE stape1';
      BACKUP TABLESPACE users;
    }
