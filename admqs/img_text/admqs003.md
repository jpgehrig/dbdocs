This diagram shows the logical, physical, and recovery-related structures of the database, and the relationships between them. Dotted horizontal lines divide the image into three sections. The top section shows logical structures, the middle section shows physical structures, and the bottom section shows recovery-related structures in the Fast Recovery Area.

The logical structures are all tablespaces. Each tablespace points to a data file or tempfile, which are physical structures. Other physical structures include a control file, the online redo log files, a server parameter file, and a password file.

The fast recovery area contains the archived redo log files, which are copies of redo log files after they are filled.
