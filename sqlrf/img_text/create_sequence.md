# Description of the illustration create_sequence.eps

    CREATE SEQUENCE [ IF NOT EXISTS ] [ schema. ] sequence
      [ SHARING = { METADATA | DATA | NONE } ]
      [ { INCREMENT BY | START WITH } integer
      | { MAXVALUE integer | NOMAXVALUE }
      | { MINVALUE integer | NOMINVALUE }
      | { CYCLE | NOCYCLE }
      | { CACHE integer | NOCACHE }
      | { ORDER | NOORDER }
      | { KEEP | NOKEEP }
      | { SCALE {EXTEND | NOEXTEND} | NOSCALE }
      | { SESSION | GLOBAL }
      ]...
