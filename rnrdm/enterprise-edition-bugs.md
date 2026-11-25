These are the Oracle Database Enterprise Edition bugs in Oracle Database 19c.

- Bug 23569490
- Bug 24291322
- Bug 27254644

**Parent topic:** [Open Bugs Affecting All Platforms](open-bugs-for-all-platforms.md)

### Bug 23569490

If you have a large number of collections and are working with clients earlier than Oracle Database 12c release 2 (12.2), then you need a larger object cache, due to a change in snapshot size and thus a need for collection image conversion.

#### Workaround:

The object cache size can be set using the `OBJECT_CACHE_OPTIMAL_SIZE` initialization parameter. This is set to a low value by default.

**Parent topic:** Oracle Database Enterprise Edition Known Bugs

### Bug 24291322

Symbolic links are not allowed in the directory object paths or filenames when opening BFILEs. The entire directory path and filename is checked and the following error is returned if any symbolic link is found:

    ORA-22288: file or LOB operation FILEOPEN failed soft link in path

#### Workaround:

If the database directory object or filename that you are trying to open contains symbolic links, then change it to provide the real path and filename.

**Parent topic:** Oracle Database Enterprise Edition Known Bugs

### Bug 27254644

During the Oracle Scheduler agent register database process (`schagent -registerdatabase`), the following warning message might be issued:

    "Warning: The JKS keystore uses a proprietary format. It is recommended to migrate
    to PKCS12 which is an industry standard format using..."

#### Workaround:

This warning message is due to a new Java runtime update. There is no change in the Oracle Scheduler agent usage of keystores (`jks` files). You can ignore this warning message.

**Parent topic:** Oracle Database Enterprise Edition Known Bugs
