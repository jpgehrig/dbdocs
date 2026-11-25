#

ARCHIVELOG DESTINATION TO ' log_archive_dest ' \| BACKUP COPIES integer \| MAXCORRUPT FOR {DATAFILE datafileSpec \[, datafileSpec\]... \| ALL DATAFILES} TO integer \| NEWNAME FOR {BLOCK CHANGE TRACKING FILE \| { {DATABASE \[ROOT\] \| PLUGGABLE DATABASE pdb_name \[, pdb_name\]...} \| DATAFILE datafileSpec \| TABLESPACE \['\] tablespace_name \['\] \| TEMPFILE tempfileSpec}} TO {' filename ' \| NEW} \| {TO RESTORE POINT restore_point_name \| untilClause}
