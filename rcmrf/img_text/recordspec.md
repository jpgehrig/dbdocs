#

ARCHIVELOG { ' filename ' \[, ' filename '\]... \| primaryKey \[, primaryKey\]...} \| BACKUPSET primaryKey \[, primaryKey\]... \| {BACKUPPIECE \| PROXY} { ' media_handle ' \[, ' media_handle '\]... \| GUID guid_name \| primaryKey \[, primaryKey\]... \| TAG \['\] tag_name \['\]} \| { {CONTROLFILECOPY \| DATAFILECOPY} { { ' filename ' \[, ' filename '\]... \| primaryKey \[, primaryKey\]...} \| TAG \['\] tag_name \['\] \[, \['\] tag_name \['\]\]... \[NODUPLICATES\]} \| DATAFILECOPY {ALL \| LIKE ' string_pattern '} \[NODUPLICATES\]}
