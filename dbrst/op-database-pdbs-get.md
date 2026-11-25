Oracle Multitenant license is required when there is more than one user-created pluggable database. Returns records from GV\$PDBS in the corresponding Container Database. This service requires db.cdb.adminUser credentials to be set in the pool configuration. A client requires SQL Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Query Parameters

- limit(optional): integer(int32)
  The maximum number of records to return.
- q(optional): string
  Filtering is the process of limiting a collection resource by using a per-request dynamic filter definition across multiple page resources, where each page contains a subset of items found in the complete collection. Filtering enables efficient traversal of large collections.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Description of all Pluggable Databases in the Container database.

Body ()

Root Schema : DatabasePluggableDatabases

Type: `object`

Show Source

- count(optional): integer
  Total number of records in the current response.
- hasMore(optional): boolean
  Indicates if there are more records to be retrieved.
- items(optional): array items
- limit(optional): integer
  The actual page size limit on number of records applied by the server.
- links(optional): array links
- offset(optional): integer
  The actual index from which the item resources are returned.

<!-- -->

    {
        "type":"object",
        "properties":{
            "items":{
                "type":"array",
                "items":{
                    "$ref":"#/definitions/DatabasePluggableDatabasesItem"
                }
            },
            "hasMore":{
                "type":"boolean",
                "description":"Indicates if there are more records to be retrieved."
            },
            "limit":{
                "type":"integer",
                "description":"The actual page size limit on number of records applied by the server."
            },
            "offset":{
                "type":"integer",
                "description":"The actual index from which the item resources are returned."
            },
            "count":{
                "type":"integer",
                "description":"Total number of records in the current response."
            },
            "links":{
                "type":"array",
                "items":{
                    "$ref":"#/definitions/LinkRelation"
                }
            }
        }
    }

Nested Schema : items

Type: `array`

Show Source

- Array of: object DatabasePluggableDatabasesItem
  This object describes a Pluggable Database associated with the current instance. The list of attributes may vary depending on database version.

<!-- -->

    {
        "type":"array",
        "items":{
            "$ref":"#/definitions/DatabasePluggableDatabasesItem"
        }
    }

Nested Schema : links

Type: `array`

Show Source

- Array of: object LinkRelation

<!-- -->

    {
        "type":"array",
        "items":{
            "$ref":"#/definitions/LinkRelation"
        }
    }

Nested Schema : DatabasePluggableDatabasesItem

Type: `object`

This object describes a Pluggable Database associated with the current instance. The list of attributes may vary depending on database version.

Show Source

- application_pdb(optional): string
  Indicates whether the PDB is an application PDB.
- application_root(optional): string
  Indicates whether the PDB is an application root.
- application_root_clone(optional): string
  Indicates whether this PDB is an application root clone (YES) or not (NO).
- application_root_con_id(optional): integer
  If this PDB is an application PDB, the container ID of an application root to which this application PDB belongs. If this PDB is an application root clone, the container ID of an application root to which this application root clone belongs. Otherwise, NULL.
- application_seed(optional): string
  Indicates whether the PDB is an application seed (an application seed is also an application PDB).
- audit_files_size(optional): integer
  Shows the current disk space usage (in bytes) by Unified Audit files (.bin format) in the current PDB.
- block_size(optional): integer
  The current block size for the PDB.
- con_id(optional): integer
  The ID of the container to which the data pertains.
- con_uid(optional): integer
  Unique identifier associated with the PDB.
- create_scn(optional): integer
  System change number (SCN) for the creation of this PDB.
- creation_time(optional): string
  Date and time at which the PDB was created.
- dbid(optional): integer
  PDB identifier calculated when the PDB is created and stored in all file headers associated with the PDB.
- diagnostics_size(optional): integer
  Shows the current disk space usage (in bytes) of the diagnostic traces generated in the PDB, which is represented by the CON_ID column of the row.
- guid(optional): string
  Globally unique identifier (GUID) of this PDB.
- guid_base64(optional): string
  The GUID of the PDB, encoded in base64.
- inst_id(optional): integer
  Instance number from which the associated GV\$PDBS view information was obtained.
- last_changed_by(optional): string
  Indicates what type of user last changed the PDB.
- links(optional): array links
- local_undo(optional): integer
  Shows whether the PDB is in local undo. This column is not relevant for CDB\$ROOT.
- max_audit_size(optional): integer
  Shows the maximum amount of disk space (in bytes) that can be used by Unified Audit files (.bin format) in the PDB.
- max_diagnostics_size(optional): integer
  Shows the maximum amount of disk space (in bytes) that can be used by diagnostic traces generated in the PDB.
- max_size(optional): integer
  Shows the maximum amount of disk space (in bytes) that can be used by data and temp files in the PDB.
- name(optional): string
  Name of the PDB.
- open_mode(optional): string
  Open mode information.
- open_time(optional): string
  Date and time when the database was last opened.
- pdb_count(optional): integer
  The number of user-created PDBs belonging to a given application root or CDB\$ROOT. For all other containers, its value is 0.
- proxy_pdb(optional): string
  Indicates whether this PDB is a proxy PDB (YES) or not (NO).
- recovery_status(optional): string
  Shows whether recovery is enabled or disabled for the PDB.
- restricted(optional): string
  Indicates whether only users possessing RESTRICTED SESSION privilege can connect to the PDB.
- snapshot_parent_con_id(optional): string
  This column shows the container ID of the master PDB that this PDB is a snapshot clone of. This column shows a nonzero value only if the PDB is a snapshot clone. For all other cases, it shows a value of 0.
- tenant_id(optional): string
  Pluggable database tenant key.
- total_size(optional): integer
  Shows the disk space (in bytes) used by the PBB, including both data and temp files.
- undo_scn(optional): integer
  System change number (SCN) at which the PDB was last converted from shared to local undo, or from local to shared undo. This column is not relevant for CDB\$ROOT.
- undo_timestamp(optional): string
  Date and time at which the PDB was last converted from shared to local undo, or from local to shared undo. This column is not relevant for CDB\$ROOT.

<!-- -->

    {
        "type":"object",
        "description":"This object describes a Pluggable Database associated with the current instance. The list of attributes may vary depending on database version.",
        "properties":{
            "inst_id":{
                "type":"integer",
                "description":"Instance number from which the associated GV$PDBS view information was obtained."
            },
            "con_id":{
                "type":"integer",
                "description":"The ID of the container to which the data pertains."
            },
            "dbid":{
                "type":"integer",
                "description":"PDB identifier calculated when the PDB is created and stored in all file headers associated with the PDB."
            },
            "con_uid":{
                "type":"integer",
                "description":"Unique identifier associated with the PDB."
            },
            "guid":{
                "type":"string",
                "description":"Globally unique identifier (GUID) of this PDB."
            },
            "name":{
                "type":"string",
                "description":"Name of the PDB."
            },
            "open_mode":{
                "type":"string",
                "description":"Open mode information."
            },
            "restricted":{
                "type":"string",
                "description":"Indicates whether only users possessing RESTRICTED SESSION privilege can connect to the PDB."
            },
            "open_time":{
                "type":"string",
                "description":"Date and time when the database was last opened."
            },
            "create_scn":{
                "type":"integer",
                "description":"System change number (SCN) for the creation of this PDB."
            },
            "total_size":{
                "type":"integer",
                "description":"Shows the disk space (in bytes) used by the PBB, including both data and temp files."
            },
            "block_size":{
                "type":"integer",
                "description":"The current block size for the PDB."
            },
            "recovery_status":{
                "type":"string",
                "description":"Shows whether recovery is enabled or disabled for the PDB."
            },
            "snapshot_parent_con_id":{
                "type":"string",
                "description":"This column shows the container ID of the master PDB that this PDB is a snapshot clone of. This column shows a nonzero value only if the PDB is a snapshot clone. For all other cases, it shows a value of 0."
            },
            "application_root":{
                "type":"string",
                "description":"Indicates whether the PDB is an application root."
            },
            "application_pdb":{
                "type":"string",
                "description":"Indicates whether the PDB is an application PDB."
            },
            "application_seed":{
                "type":"string",
                "description":"Indicates whether the PDB is an application seed (an application seed is also an application PDB)."
            },
            "application_root_con_id":{
                "type":"integer",
                "description":"If this PDB is an application PDB, the container ID of an application root to which this application PDB belongs. If this PDB is an application root clone, the container ID of an application root to which this application root clone belongs. Otherwise, NULL."
            },
            "application_root_clone":{
                "type":"string",
                "description":"Indicates whether this PDB is an application root clone (YES) or not (NO)."
            },
            "proxy_pdb":{
                "type":"string",
                "description":"Indicates whether this PDB is a proxy PDB (YES) or not (NO)."
            },
            "local_undo":{
                "type":"integer",
                "description":"Shows whether the PDB is in local undo. This column is not relevant for CDB$ROOT."
            },
            "undo_scn":{
                "type":"integer",
                "description":"System change number (SCN) at which the PDB was last converted from shared to local undo, or from local to shared undo. This column is not relevant for CDB$ROOT."
            },
            "undo_timestamp":{
                "type":"string",
                "description":"Date and time at which the PDB was last converted from shared to local undo, or from local to shared undo. This column is not relevant for CDB$ROOT."
            },
            "creation_time":{
                "type":"string",
                "description":"Date and time at which the PDB was created."
            },
            "diagnostics_size":{
                "type":"integer",
                "description":"Shows the current disk space usage (in bytes) of the diagnostic traces generated in the PDB, which is represented by the CON_ID column of the row."
            },
            "pdb_count":{
                "type":"integer",
                "description":"The number of user-created PDBs belonging to a given application root or CDB$ROOT. For all other containers, its value is 0."
            },
            "audit_files_size":{
                "type":"integer",
                "description":"Shows the current disk space usage (in bytes) by Unified Audit files (.bin format) in the current PDB."
            },
            "max_size":{
                "type":"integer",
                "description":"Shows the maximum amount of disk space (in bytes) that can  be used by data and temp files in the PDB."
            },
            "max_diagnostics_size":{
                "type":"integer",
                "description":"Shows the maximum amount of disk space (in bytes) that can be used by diagnostic traces generated in the PDB."
            },
            "max_audit_size":{
                "type":"integer",
                "description":"Shows the maximum amount of disk space (in bytes) that can be used by Unified Audit files (.bin format) in the PDB."
            },
            "last_changed_by":{
                "type":"string",
                "description":"Indicates what type of user last changed the PDB."
            },
            "tenant_id":{
                "type":"string",
                "description":"Pluggable database tenant key."
            },
            "guid_base64":{
                "type":"string",
                "description":"The GUID of the PDB, encoded in base64."
            },
            "links":{
                "type":"array",
                "items":{
                    "$ref":"#/definitions/LinkRelation"
                }
            }
        }
    }

Nested Schema : links

Type: `array`

Show Source

- Array of: object LinkRelation

<!-- -->

    {
        "type":"array",
        "items":{
            "$ref":"#/definitions/LinkRelation"
        }
    }

Nested Schema : LinkRelation

Type: `object`

Show Source

- href: string
- rel: string

<!-- -->

    {
        "type":"object",
        "properties":{
            "rel":{
                "type":"string"
            },
            "href":{
                "type":"string"
            }
        },
        "required":[
            "rel",
            "href"
        ]
    }

Back to Top
