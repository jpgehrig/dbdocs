# Description of the illustration dim_key.eps

    dim_ref
      [classification_clause]...
      KEY
        {[(] [alias.] fact_column  [)]
         |
         (  [alias.] fact_column [, [alias.] fact_column]... )
        }
      REFERENCES
         { [DISTINCT]
           [(]  attribute  [)]
           |
           ( attribute [, attribute]... )
         }
      HIERARCHIES ( hier_ref [, hier_ref]... )
