#

    et_record_spec ::=

      RECORDS { FIXED integer | VARIABLE integer | DELIMITED BY { { DETECTED } NEWLINE | string } |
    XMLTAG string }
      [et_record_spec_options]
