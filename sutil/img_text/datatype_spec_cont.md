#

    datatype_spec_cont ::=

     CHAR [(length)] [delim_spec]
     |VARCHARC (length_of_length [, max_size_bytes])
     |VARRAWC  (length_of_length [, max_size_bytes])
     |[LONG] VARRAW [(max_bytes)]
     |DATE [EXTERNAL] [(length)] [\"mask\"] [delim_spec]
     |{ TIME|TIMESTAMP } [(fractional_second_precision)] [WITH [LOCAL] TIME ZONE] [\"mask\"]
     |INTERVAL [ { YEAR [(year_precision)] TO MONTH | DAY [(day_precision)] TO SECOND [(fractional_second_precision)]} ]
