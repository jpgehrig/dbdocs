# Description of the illustration alter_session.eps

    ALTER SESSION
      { ADVISE { COMMIT | ROLLBACK | NOTHING }
      | CLOSE DATABASE LINK dblink
      | { ENABLE | DISABLE } COMMIT IN PROCEDURE
      | { ENABLE | DISABLE } GUARD
      | { ENABLE | DISABLE | FORCE } PARALLEL
        { DML | DDL | QUERY } [ PARALLEL integer ]
      | { ENABLE RESUMABLE [ TIMEOUT integer ] [ NAME string ]
        | DISABLE RESUMABLE
        }
      | { ENABLE | DISABLE } SHARD DDL
      | SYNC WITH PRIMARY
      | alter_session_set_clause
      } ;
