#

    fld_cond  ::=

      [(]
      {full_fieldname | pos_spec } operator { 'char_string' | X'hex_string' | BLANKS}
      [)] AND
      [(]
      {full_fieldname | pos_spec } operator { 'char_string' | X'hex_string' | BLANKS}
      [)]...
