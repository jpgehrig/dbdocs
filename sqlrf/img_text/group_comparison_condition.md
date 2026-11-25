# Description of the illustration group_comparison_condition.eps

    { expr
         { = | != | ^= |  | < | >= | ANY | SOME | ALL }
         ({ expression_list | subquery })
    | ( expr [, expr ]... )
      { = | != | ^= | ANY | SOME | ALL }
      ({ expression_list
         [, expression_list ]...
       | subquery
       }
      )
    }
