#

    concatenate ::=

      CONCATENATE { integer | (integer) }
      |CONTINUEIF
      { { THIS | NEXT } [PRESERVE] [(] (pos_spec)
      |[LAST [PRESERVE] [(] } operator { str | X'hex_str' } [)]
