The ReFS prevents corruption of the file metadata that occurs in standard NTFS volumes which makes data inaccessible.

This release supports Oracle Database installation on Resilient File System (ReFS). ReFS uses checksums for file metadata, and an allocate-on-write method to update data which minimizes the risk of corruption.

ReFS supports volumes from 256 zettabytes to a maximum of 4 petabytes. ReFS stores and protects data from common errors that cause data loss. ReFS is resilient to power outages. ReFS also protects data based on volumes, directory, and files.

- [Setting File Permissions](setting-file-permissions.md)

**Parent topic:** [Postinstallation Configuration Tasks on Windows](postinstallation-configuration-tasks-on-windows.md)
