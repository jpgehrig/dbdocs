# Description of the illustration alter_sequence

      ALTER SEQUENCE [ schema. ] sequence
      { { (INCREMENT BY) | ( START WITH ) } integer
      | { MAXVALUE integer | NOMAXVALUE }
      | { MINVALUE integer | NOMINVALUE }
      |  RESTART
      | { CYCLE | NOCYCLE }
      | { CACHE integer | NOCACHE }
      | { ORDER | NOORDER }
      | { KEEP | NOKEEP }
      | { SCALE {EXTEND | NOEXTEND} | NOSCALE }
      | { SHARD {EXTEND | NOEXTEND} | NOSHARD }
      | { SESSION | GLOBAL }
      } ...
