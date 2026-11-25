Returns the corresponding record from DBA_TAB_COLUMNS or ALL_TAB_COLUMNS view depending on role at runtime. A client requires SQL Administrator or SQL Developer role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- column_name: string
  Name of the column.
- owner: string
  Owner for the index.
- table_name: string
  Name of the table the column belongs to.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Information on a specific column.

Body ()

Root Schema : DatabaseObjectsColumnsItem

Type: `object`

Describes the column of table, view, or cluster in the database.

Show Source

- avg_col_len(optional): integer
  Average length of the column (in bytes).
- char_col_decl_length(optional): number
  Declaration length of the character type column.
- char_length(optional): integer
  Displays the length of the column in characters.
- char_used(optional): string
  Indicates that the column uses BYTE length semantics (B) or CHAR length semantics (C), or whether the data type is not any of the following (NULL): CHAR, VARCHAR2, NCHAR, NVARCHAR2.
- character_set_name(optional): string
  Name of the character set.
- collation(optional): string
  Collation for the column. Only applies to columns with character data types.
- column_id(optional): integer
  Sequence number of the column as created.
- column_name(optional): string
  Column name.
- data_default(optional): integer
  Default value for the column.
- data_length(optional): integer
  Length of the column (in bytes).
- data_precision(optional): integer
  Decimal precision for NUMBER data type; binary precision for FLOAT data type; NULL for all other data types.
- data_scale(optional): integer
  Digits to the right of the decimal point in a number.
- data_type(optional): string
  Data type of the column.
- data_type_mod(optional): string
  Data type modifier of the column.
- data_type_owner(optional): string
  Owner of the data type of the column.
- data_upgraded(optional): string
  Indicates whether the column data has been upgraded to the latest type version format (YES) or not (NO).
- default_length(optional): number
  Length of the default value for the column.
- default_on_null(optional): string
  Indicates whether the column has DEFAULT ON NULL semantics (YES) or not (NO).
- density(optional): number
  If a histogram is available on COLUMN_NAME, then this column displays the selectivity of a value that spans fewer than 2 endpoints in the histogram. It does not represent the selectivity of values that span 2 or more endpoints. If a histogram is not available on COLUMN_NAME, then the value of this column is 1/NUM_DISTINCT.
- evaluation_edition(optional): string
  Name of the edition in which editioned objects referenced in an expression column are resolved.
- global_stats(optional): string
  GLOBAL_STATS will be YES if statistics are gathered or incrementally maintained, otherwise it will be NO.
- high_value(optional): string
  High value in the column.
- histogram(optional): string
  Indicates existence/type of histogram.
- identity_column(optional): string
  Indicates whether this is an identity column (YES) or not (NO).
- last_analyzed(optional): string
  Date on which this column was most recently analyzed.
- links(optional): array links
- low_value(optional): string
  Low value in the column.
- nullable(optional): string
  Indicates whether a column allows NULLs. The value is N if there is a NOT NULL constraint on the column or if the column is part of a PRIMARY KEY. The constraint should be in an ENABLE VALIDATE state.
- num_buckets(optional): integer
  Number of buckets in the histogram for the column.
- num_distinct(optional): number
  Number of distinct values in the column.
- num_nulls(optional): integer
  Number of NULLs in the column.
- owner(optional): string
  Owner of the table, view, or cluster.
- sample_size(optional): integer
  Sample size used in analyzing this column.
- sensitive_column(optional): string
  Indicates whether this is a sensitive column (YES) or not (NO).
- table_name(optional): string
  Name of the table, view, or cluster.
- unusable_before(optional): string
  Name of the oldest edition in which the index may be used as part of a query plan.
- unusable_beginning(optional): string
  Name of the edition for which the index may not be used as part of a query plan in this edition or any of its descendants.
- user_stats(optional): string
  Indicates whether statistics were entered directly by the user (YES) or not (NO).
- v80_fmt_image(optional): string
  Indicates whether the column data is in release 8.0 image format (YES) or not (NO).

<!-- -->

    {
        "type":"object",
        "description":"Describes the column of table, view, or cluster in the database.",
        "properties":{
            "owner":{
                "type":"string",
                "description":"Owner of the table, view, or cluster."
            },
            "table_name":{
                "type":"string",
                "description":"Name of the table, view, or cluster."
            },
            "column_name":{
                "type":"string",
                "description":"Column name."
            },
            "data_type":{
                "type":"string",
                "description":"Data type of the column."
            },
            "data_type_mod":{
                "type":"string",
                "description":"Data type modifier of the column."
            },
            "data_type_owner":{
                "type":"string",
                "description":"Owner of the data type of the column."
            },
            "data_length":{
                "type":"integer",
                "description":"Length of the column (in bytes)."
            },
            "data_precision":{
                "type":"integer",
                "description":"Decimal precision for NUMBER data type; binary precision for FLOAT data type; NULL for all other data types."
            },
            "data_scale":{
                "type":"integer",
                "description":"Digits to the right of the decimal point in a number."
            },
            "nullable":{
                "type":"string",
                "description":"Indicates whether a column allows NULLs. The value is N if there is a NOT NULL constraint on the column or if the column is part of a PRIMARY KEY. The constraint should be in an ENABLE VALIDATE state."
            },
            "column_id":{
                "type":"integer",
                "description":"Sequence number of the column as created."
            },
            "default_length":{
                "type":"number",
                "description":"Length of the default value for the column."
            },
            "data_default":{
                "type":"integer",
                "description":"Default value for the column."
            },
            "num_distinct":{
                "type":"number",
                "description":"Number of distinct values in the column."
            },
            "low_value":{
                "type":"string",
                "description":"Low value in the column."
            },
            "high_value":{
                "type":"string",
                "description":"High value in the column."
            },
            "density":{
                "type":"number",
                "description":"If a histogram is available on COLUMN_NAME, then this column displays the selectivity of a value that spans fewer than 2 endpoints in the histogram. It does not represent the selectivity of values that span 2 or more endpoints. If a histogram is not available on COLUMN_NAME, then the value of this column is 1/NUM_DISTINCT."
            },
            "num_nulls":{
                "type":"integer",
                "description":"Number of NULLs in the column."
            },
            "num_buckets":{
                "type":"integer",
                "description":"Number of buckets in the histogram for the column."
            },
            "last_analyzed":{
                "type":"string",
                "description":"Date on which this column was most recently analyzed."
            },
            "sample_size":{
                "type":"integer",
                "description":"Sample size used in analyzing this column."
            },
            "character_set_name":{
                "type":"string",
                "description":"Name of the character set."
            },
            "char_col_decl_length":{
                "type":"number",
                "description":"Declaration length of the character type column."
            },
            "global_stats":{
                "type":"string",
                "description":"GLOBAL_STATS will be YES if statistics are gathered or incrementally maintained, otherwise it will be NO."
            },
            "user_stats":{
                "type":"string",
                "description":"Indicates whether statistics were entered directly by the user (YES) or not (NO)."
            },
            "avg_col_len":{
                "type":"integer",
                "description":"Average length of the column (in bytes)."
            },
            "char_length":{
                "type":"integer",
                "description":"Displays the length of the column in characters."
            },
            "char_used":{
                "type":"string",
                "description":"Indicates that the column uses BYTE length semantics (B) or CHAR length semantics (C), or whether the data type is not any of the following (NULL): CHAR, VARCHAR2, NCHAR, NVARCHAR2."
            },
            "v80_fmt_image":{
                "type":"string",
                "description":"Indicates whether the column data is in release 8.0 image format (YES) or not (NO)."
            },
            "data_upgraded":{
                "type":"string",
                "description":"Indicates whether the column data has been upgraded to the latest type version format (YES) or not (NO)."
            },
            "histogram":{
                "type":"string",
                "description":"Indicates existence/type of histogram."
            },
            "default_on_null":{
                "type":"string",
                "description":"Indicates whether the column has DEFAULT ON NULL semantics (YES) or not (NO)."
            },
            "identity_column":{
                "type":"string",
                "description":"Indicates whether this is an identity column (YES) or not (NO)."
            },
            "sensitive_column":{
                "type":"string",
                "description":"Indicates whether this is a sensitive column (YES) or not (NO)."
            },
            "evaluation_edition":{
                "type":"string",
                "description":"Name of the edition in which editioned objects referenced in an expression column are resolved."
            },
            "unusable_before":{
                "type":"string",
                "description":"Name of the oldest edition in which the index may be used as part of a query plan."
            },
            "unusable_beginning":{
                "type":"string",
                "description":"Name of the edition for which the index may not be used as part of a query plan in this edition or any of its descendants."
            },
            "collation":{
                "type":"string",
                "description":"Collation for the column. Only applies to columns with character data types."
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
