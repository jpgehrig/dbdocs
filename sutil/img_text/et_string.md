#

    et_string ::=

    {
     "text"
    |'text'
    |{X | 0X} "hex digit hex digit" ["hex digit hex digit"]...
    |{X | 0X} 'hex digit hex digit' ['hex digit hex digit']...
    }
