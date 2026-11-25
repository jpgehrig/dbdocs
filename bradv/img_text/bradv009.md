# Description of the illustration bradv009.eps

This illustration presents using the control file as the repository for backups of the catalog. RMAN is used to back up the target database. Metadata about backups of the target database are stored in the recovery catalog database. RMAN is also used to back up the catalog database. Metadata about backups of the recovery catalog database are stored in the catalog database control file. RMAN takes autobackups of the control file of the recovery catalog database.
