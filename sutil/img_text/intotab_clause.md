#

    intotab_clause ::=

     INTO TABLE name [SORTED [INDEXES] (name)]
     [SINGLEROW] [ ( { PARTITION name | SUBPARTITION name } ) ]
     [ {RESUME [ { YES | NO [REPLACE] } ] | INSERT | REPLACE [ USING  {DELETE | TRUNCATE} ]
     | TRUNCATE | APPEND} ]
    [OPTIONS (STORAGE=storage_spec, FILE=database_filename)]
    [ [EVALUATE CHECK_CONSTRAINTS] [into_table_clause_continued]
