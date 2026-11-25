# Description of the illustration create_restore_point.eps

    CREATE [ CLEAN ] RESTORE POINT restore_point
       [ FOR PLUGGABLE DATABASE pdb_name ]
       [ AS OF {TIMESTAMP | SCN} expr ]
       [ PRESERVE
       | GUARANTEE FLASHBACK DATABASE
       ];
