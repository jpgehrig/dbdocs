# Description of the illustration other_boolean_form.eps

    { collection.EXISTS ( index )
    | expression { IS [ NOT ] NULL
                 | [ NOT ] { BETWEEN expression AND expression
                           | IN ( expression [, expression ]... )
                           | LIKE pattern
                           }
                 | relational_operator expression
                 }
    | { named_cursor | SQL } % { FOUND | ISOPEN | NOTFOUND }
    }
