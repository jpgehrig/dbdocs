#

{APPLICATION ROOT DATABASE {identifier \| quoted_string} \| DATABASE \| PLUGGABLE DATABASEpdb_name} { {TO BEFORE SCNinteger \| TO BEFORE SEQUENCEinteger \[THREADinteger\] \| TO BEFORE RESETLOGS \| TO BEFORETIME ' date_string '} \| {TO SCNinteger \| TO SEQUENCEinteger \[THREADinteger\] \| TORESTORE POINTrestore_point_name \| TO TIME ' date_string '}}
