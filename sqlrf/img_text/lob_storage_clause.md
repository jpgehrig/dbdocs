# Description of the illustration lob_storage_clause.eps

    LOB
    { (LOB_item [, LOB_item ]...)
         STORE AS { {SECUREFILE | BASICFILE}
                  | (LOB_storage_parameters)
                  }...
    | (LOB_item)
         STORE AS { {SECUREFILE | BASICFILE}
                  | LOB_segname
                  | (LOB_storage_parameters)
                  }...
    }
