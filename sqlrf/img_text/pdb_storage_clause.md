# Description of the illustration pdb_storage_clause.eps

    STORAGE
      { ( { MAXSIZE { UNLIMITED | size_clause }
            |
            MAX_AUDIT_SIZE { UNLIMITED | size_clause }
            |
            MAX_DIAG_SIZE { UNLIMITED | size_clause }
          }...
        )
      |
      UNLIMITED
      }
