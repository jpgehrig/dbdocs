# Description of the illustration cursor_for_loop_statement.eps

    [ FOR record IN
      { cursor [ ( cursor_parameter_dec
                   [ [,] cursor_parameter_dec ]... )]
      | ( select_statement )
      }
        LOOP statement... END LOOP [label] ;
