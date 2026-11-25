Oracle Diagnostic Pack licence is required for this service. Returns DBA_HIST_TBSPC_SPACE_USAGE records where tablespace size has changed. These records are historical tablespace usage statistics. Recent changes in tablespace storage or usage will not appear until a snapshot is created. A client requires SQL Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- tablespace_name: string
  Name of the tablespace.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Tablespace space usage history for the specified tablespace.

Body ()

Root Schema : DatabaseTablespaceHistoryItem

Type: `object`

Describes historical tablespace usage statistics.

Show Source

- con_dbid(optional): integer
  The database ID of the PDB for the sampled session.
- con_id(optional): integer
  The ID of the container that CON_DBID identifies.
- dbid(optional): integer
  Database ID for the snapshot.
- name(optional): string
  Tablespace name.
- prev_tablespace_size(optional): integer
  The previous tablespace size (in database blocks).
- rtime(optional): string
  Runtime.
- snap_id(optional): integer
  Unique snapshot ID.
- tablespace_id(optional): integer
  Tablespace ID.
- tablespace_maxsize(optional): integer
  Maximum size of the tablespace (in database blocks).
- tablespace_size(optional): integer
  Tablespace size (in database blocks).
- tablespace_usedsize(optional): integer
  Used size of the tablespace (in database blocks).

<!-- -->

    {
        "type":"object",
        "description":"Describes historical tablespace usage statistics.",
        "properties":{
            "snap_id":{
                "type":"integer",
                "description":"Unique snapshot ID."
            },
            "dbid":{
                "type":"integer",
                "description":"Database ID for the snapshot."
            },
            "tablespace_id":{
                "type":"integer",
                "description":"Tablespace ID."
            },
            "tablespace_size":{
                "type":"integer",
                "description":"Tablespace size (in database blocks)."
            },
            "tablespace_maxsize":{
                "type":"integer",
                "description":"Maximum size of the tablespace (in database blocks)."
            },
            "tablespace_usedsize":{
                "type":"integer",
                "description":"Used size of the tablespace (in database blocks)."
            },
            "rtime":{
                "type":"string",
                "description":"Runtime."
            },
            "con_dbid":{
                "type":"integer",
                "description":"The database ID of the PDB for the sampled session."
            },
            "con_id":{
                "type":"integer",
                "description":"The ID of the container that CON_DBID identifies."
            },
            "prev_tablespace_size":{
                "type":"integer",
                "description":"The previous tablespace size (in database blocks)."
            },
            "name":{
                "type":"string",
                "description":"Tablespace name."
            }
        }
    }

Back to Top
