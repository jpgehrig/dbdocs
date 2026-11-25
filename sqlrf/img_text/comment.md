# Description of the illustration comment.eps

    COMMENT ON
      { AUDIT POLICY policy
      | COLUMN [ schema. ]
          { table. | view. | materialized_view. } column
      | EDITION edition_name
      | INDEXTYPE [ schema. ] indextype
      | MATERIALIZED VIEW materialized_view
      | MINING MODEL [ schema. ] model
      | OPERATOR [ schema. ] operator
      | TABLE [ schema. ] { table | view }
      }
      IS string ;
