#

    load_statement ::=

      [{ UNRECOVERABLE | RECOVERABLE }] { LOAD | CONTINUE_LOAD } [DATA]
    [DEFAULT EXPRESSION CACHE n] | [CHARACTERSET char_set_name]
    [LENGTH [SEMANTICS] { BYTE | CHAR | CHARACTER }] [BYTEORDER { BIG | LITTLE } [ENDIAN]]
    [BYTEORDERMARK { CHECK | NOCHECK }]
    [FIELD NAMES {FIRST FILE | FIRST FILE IGNORE | ALL FILES | ALL FILES IGNORE | NONE}]
    [infile_clause] [, infile_clause]... [READSIZE size] [READBUFFERS integer]
    [{ INSERT | APPEND | REPLACE | TRUNCATE }]
    [concatenate_clause][PRESERVE BLANKS] into_table_clause [, into_table_clause]... [BEGINDATA]
