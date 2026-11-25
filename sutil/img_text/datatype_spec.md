#

    datatype_spec ::=

      delim_spec
     |INTEGER { [(length)] [{ SIGNED | UNSIGNED }] |
     [EXTERNAL [(length)] [delim_spec]] }
     |FLOAT [EXTERNAL [(length)] [delim_spec] ]
     |{ DECIMAL | ZONED } { [EXTERNAL [(length)] [delim_spec]] |
     (precision [, scale]) }
     |{ DOUBLE | BYTEINT | SMALLINT { SIGNED | UNSIGNED } }
     |RAW [(length)]
     |GRAPHIC [EXTERNAL] [(graphic_char_length)]
     |{ VARGRAPHIC | VARCHAR } [(max_length)]
     datatype_spec_cont
