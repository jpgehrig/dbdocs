# Description of the illustration compound_expression.eps

    { (expr)
    | { + | - | PRIOR } expr
    | expr { * | / | + | - | || } expr
    | expr COLLATE collation_name
    }

    Note: The double vertical bars are part of the syntax
          (indicating concatenation) rather than BNF notation.
