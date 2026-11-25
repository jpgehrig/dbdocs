# Description of the illustration supplemental_table_logging.eps

    { ADD SUPPLEMENTAL LOG
      { supplemental_log_grp_clause | supplemental_id_key_clause }
        [ SUPPLEMENTAL LOG
           { supplemental_log_grp_clause | supplemental_id_key_clause }
        ]...
    | DROP SUPPLEMENTAL LOG
      { supplemental_id_key_clause | GROUP log_group }
        [ SUPPLEMENTAL LOG
           { supplemental_id_key_clause | GROUP log_group }
        ]...
    }
