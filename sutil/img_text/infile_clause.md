#

    infile_clause ::=

      INFILE { * | input_filename } [os_file_proc_clause]
     [BADFILE [directory_path] [filename ] ]
     [DISCARDFILE [directory_path] [filename]]
     [" { var | fix | [str [ 'string' | X'hex_string ] ] | integer } "]
