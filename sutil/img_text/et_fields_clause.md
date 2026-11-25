#

The syntax that is in the image is in Backus–Naur form for et_fields_clause. The syntax is as follows:

et_fields_clause ::=

( FIELDS
IGNORE_CHARS_AFTER_EOR
CSV {WITH EMBEDDED \| WITHOUT EMBEDDED}
delim_spec
trim_spec
ALL FIELDS OVERRIDE THESE FIELDS
MISSING FIELD VALUES ARE NULL
REJECT ROWS WITH ALL NULL FIELDS
DATE FORMAT {DATE \| TIMESTAMP} MASK string
\[NULLIF \| NONULLIF
) field_list
