Returns the specified argument information from DBA_ARGUMENTS or ALL_ARGUMENTS view depending on role at runtime. A client requires SQL Administrator or SQL Developer role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- argument_name: string
  Name of the argument.
- object_id: number
  Identifier of the object the argument belongs to.
- subprogram_id: number
  Identifier of the subprogram the argument belongs to.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Information for the specified argument.

Body ()

Root Schema : DatabaseArgumentsItem

Type: `object`

This object represents arguments of the functions and procedures that are available in the database. The list of attributes may vary depending on database version.

Show Source

- argument_name(optional): string
  If the argument is a scalar type, then the argument name is the name of the argument. A null argument name is used to denote a function return. If the function return or argument is a composite type, this view will have one row for each attribute of the composite type. Attributes are recursively expanded if they are composite.
- char_length(optional): integer
  Character limit for string datatypes.
- char_used(optional): string
  Indicates whether the byte limit (B) or char limit (C) is official for the string.
- character_set_name(optional): string
  Character set name for the argument.
- data_length(optional): integer
  Length of the column (in bytes).
- data_level(optional): integer
  Nesting depth of the argument for composite types.
- data_precision(optional): integer
  Length in decimal digits (NUMBER) or binary digits (FLOAT).
- data_scale(optional): integer
  Digits to the right of the decimal point in a number.
- data_type(optional): string
  Datatype of the argument.
- default_length(optional): integer
  Reserved for future use.
- default_value(optional): integer
  Reserved for future use.
- defaulted(optional): string
  Specifies whether or not the argument is defaulted.
- in_out(optional): string
  Direction of the argument: IN, OUT, IN/OUT.
- links(optional): array links
- object_id(optional): integer
  Dictionary object number of the object.
- object_name(optional): string
  Name of the procedure or function.
- origin_con_id(optional): integer
  The ID of the container where the data originates.
- overload(optional): string
  Indicates the nth overloading ordered by its appearance in the source; otherwise, it is NULL.
- owner(optional): string
  Owner of the object.
- package_name(optional): string
  Name of the package.
- pls_type(optional): string
  For numeric arguments, the name of the PL/SQL type of the argument. Null otherwise.
- position(optional): integer
  If DATA_LEVEL is zero, then this column holds the position of this item in the argument list, or zero for a function return value.If DATA_LEVEL is greater than zero, then this column holds the position of this item with respect to its siblings at the same DATA_LEVEL. So, for a referenced record field, this is the index of the field within the record. For a referenced collection element, this is 1 (because collection elements do not have siblings.)
- radix(optional): integer
  Argument radix for a number.
- sequence(optional): integer
  Defines the sequential order of the argument and its attributes. Argument sequence starts from 1. Return type and its recursively expanded (preorder tree walk) attributes will come first, and each argument with its recursively expanded (preorder tree walk) attributes will follow.
- subprogram_id(optional): integer
  Unique subprogram identifier.
- type_link(optional): string
  Relevant only for package local types when the package identified in the TYPE_NAME column is a remote package. This column displays the database link used to refer to the remote package.
- type_name(optional): string
  Name of the type of the argument. If the type is a package local type (that is, it is declared in a package specification), then this column displays the name of the package.
- type_object_type(optional): string
  Displays the type of the type described by the TYPE_OWNER, TYPE_NAME, and TYPE_SUBNAME columns.
- type_owner(optional): string
  Owner of the type of the argument.
- type_subname(optional): string
  Relevant only for package local types. Displays the name of the type declared in the package identified in the TYPE_NAME column.

<!-- -->

    {
        "type":"object",
        "description":"This object represents arguments of the functions and procedures that are available in the database. The list of attributes may vary depending on database version.",
        "properties":{
            "owner":{
                "type":"string",
                "description":"Owner of the object."
            },
            "object_name":{
                "type":"string",
                "description":"Name of the procedure or function."
            },
            "package_name":{
                "type":"string",
                "description":"Name of the package."
            },
            "object_id":{
                "type":"integer",
                "description":"Dictionary object number of the object."
            },
            "overload":{
                "type":"string",
                "description":"Indicates the nth overloading ordered by its appearance in the source; otherwise, it is NULL."
            },
            "subprogram_id":{
                "type":"integer",
                "description":"Unique subprogram identifier."
            },
            "argument_name":{
                "type":"string",
                "description":"If the argument is a scalar type, then the argument name is the name of the argument. A null argument name is used to denote a function return. If the function return or argument is a composite type, this view will have one row for each attribute of the composite type. Attributes are recursively expanded if they are composite."
            },
            "position":{
                "type":"integer",
                "description":"If DATA_LEVEL is zero, then this column holds the position of this item in the argument list, or zero for a function return value.If DATA_LEVEL is greater than zero, then this column holds the position of this item with respect to its siblings at the same DATA_LEVEL. So, for a referenced record field, this is the index of the field within the record. For a referenced collection element, this is 1 (because collection elements do not have siblings.)"
            },
            "sequence":{
                "type":"integer",
                "description":"Defines the sequential order of the argument and its attributes. Argument sequence starts from 1. Return type and its recursively expanded (preorder tree walk) attributes will come first, and each argument with its recursively expanded (preorder tree walk) attributes will follow."
            },
            "data_level":{
                "type":"integer",
                "description":"Nesting depth of the argument for composite types."
            },
            "data_type":{
                "type":"string",
                "description":"Datatype of the argument."
            },
            "defaulted":{
                "type":"string",
                "description":"Specifies whether or not the argument is defaulted."
            },
            "default_value":{
                "type":"integer",
                "description":"Reserved for future use."
            },
            "default_length":{
                "type":"integer",
                "description":"Reserved for future use."
            },
            "in_out":{
                "type":"string",
                "description":"Direction of the argument: IN, OUT, IN/OUT."
            },
            "data_length":{
                "type":"integer",
                "description":"Length of the column (in bytes)."
            },
            "data_precision":{
                "type":"integer",
                "description":"Length in decimal digits (NUMBER) or binary digits (FLOAT)."
            },
            "data_scale":{
                "type":"integer",
                "description":"Digits to the right of the decimal point in a number."
            },
            "radix":{
                "type":"integer",
                "description":"Argument radix for a number."
            },
            "character_set_name":{
                "type":"string",
                "description":"Character set name for the argument."
            },
            "type_owner":{
                "type":"string",
                "description":"Owner of the type of the argument."
            },
            "type_name":{
                "type":"string",
                "description":"Name of the type of the argument. If the type is a package local type (that is, it is declared in a package specification), then this column displays the name of the package."
            },
            "type_subname":{
                "type":"string",
                "description":"Relevant only for package local types. Displays the name of the type declared in the package identified in the TYPE_NAME column."
            },
            "type_link":{
                "type":"string",
                "description":"Relevant only for package local types when the package identified in the TYPE_NAME column is a remote package. This column displays the database link used to refer to the remote package."
            },
            "type_object_type":{
                "type":"string",
                "description":"Displays the type of the type described by the TYPE_OWNER, TYPE_NAME, and TYPE_SUBNAME columns."
            },
            "pls_type":{
                "type":"string",
                "description":"For numeric arguments, the name of the PL/SQL type of the argument. Null otherwise."
            },
            "char_length":{
                "type":"integer",
                "description":"Character limit for string datatypes."
            },
            "char_used":{
                "type":"string",
                "description":"Indicates whether the byte limit (B) or char limit (C) is official for the string."
            },
            "origin_con_id":{
                "type":"integer",
                "description":"The ID of the container where the data originates."
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
