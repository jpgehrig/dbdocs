#

    et_record_spec_options ::=

        CHARACTERSET string
        |PREPROCESSOR [directory_spec:] file_spec
        |DATA IS { LITTLE | BIG } ENDIAN
        |BYTEORDERMARK { CHECK | NOCHECK }
        |STRING SIZES ARE IN { BYTES | CHARACTERS }
        |LOAD WHEN condition_spec
        | et_output_files
        |{READSIZE integer | DISABLE_DIRECTORY_LINK_CHECK | DATE_CACHE integer | SKIP integer}
        |IO_OPTIONS {DIRECTIO | NODIRECTIO}
        |{ DNFS_ENABLE | DNFS_DISABLE }
        |DNFS_READBUFFERS integer
       [,]...
