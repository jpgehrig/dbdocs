# Description of the illustration xmltype_storage.eps

    STORE
    { AS
    { OBJECT RELATIONAL
    | [SECUREFILE | BASICFILE]
      { CLOB | BINARY XML }
        [ { LOB_segname [ (LOB_parameters) ]
          | (LOB_parameters)
          }
        ]
    }
    | { ALL VARRAYS AS { LOBS | TABLES } }
    }
