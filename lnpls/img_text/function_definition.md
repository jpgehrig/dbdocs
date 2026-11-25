# Description of the illustration function_definition

    function_heading [ DETERMINISTIC
                     | PIPELINED
                     | PARALLEL_ENABLE
                     | RESULT_CACHE [ relies_on_clause ]
                     ]...
      { IS | AS } { [ declare_section ] body | call_spec }
