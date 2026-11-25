# Description of the illustration alter_flashback_archive.eps

    ALTER FLASHBACK ARCHIVE flashback_archive
      { SET DEFAULT
      | { ADD | MODIFY } TABLESPACE tablespace [flashback_archive_quota]
      | REMOVE TABLESPACE tablespace_name
      | MODIFY RETENTION flashback_archive_retention
      | PURGE { ALL | BEFORE { SCN expr | TIMESTAMP expr } }
      | [NO] OPTIMIZE DATA
      };
