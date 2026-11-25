## Monitoring Direct NFS Client Usage

You use data dictionary view to monitor the Direct NFS client.

- Use the following global dynamic performance views for managing Direct NFS Client usage with your Oracle RAC database:
  - `GV$DNFS_SERVERS`: Lists the servers that are accessed using Direct NFS Client.

  - `GV$DNFS_FILES`: Lists the files that are currently open using Direct NFS Client.

  - `GV$DNFS_CHANNELS`: Lists the open network paths, or channels, to servers for which Direct NFS Client is providing files.

  - `GV$DNFS_STATS`: Lists performance statistics for Direct NFS Client.

**Parent topic:** [Configuring Direct NFS Client for Oracle RAC Data Files](configuring-direct-nfs-client-for-oracle-rac-data-files.md)
