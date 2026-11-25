# Description of the illustration bradv037.eps

The figure shows the major entities involved in RMAN transportable tablespace from backup:

- The source database, with RMAN-usable backups and archived redo logs

- The RMAN client, connected to the source database

- The auxiliary instance created by RMAN for use in creating the transportable tablespace set

- The auxiliary destination, where the output files for the auxiliary instance that are not part of the transportable set are stored

- The tablespace destination, where the data files and Data Pump Export dump file are written, along with a sample import script

The part played by each of these entities is described in the text which follows.
