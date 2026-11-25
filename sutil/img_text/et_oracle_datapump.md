#

et_oracle_datapump ::=
\[comments\]
(\[ {ENCRYPTION {ENABLED \| DISABLED} \|
{NOLOGFILE \| LOGFILE \[directory object name :\] file name} \|
COMPRESSION {ENABLED \[BASIC \|LOW \| MEDIUM \| HIGH\] \| DISABLED}}\|
HADOOP_TRAILERS {ENABLED \| DISABLED}
VERSION {COMPATIBLE \| LATEST \| version number}\])
