# Description of the illustration standard_actions.eps

    ACTIONS
      { { object_action | ALL }
        ON { DIRECTORY directory_name
           | MINING MODEL [ schema. ] object_name
           | [ schema. ] object_name }
      | { system_action | ALL }
      }
        [ { object_action | ALL }
          ON { DIRECTORY directory_name
             | MINING MODEL [ schema. ] object_name
             | [ schema. ] object_name }
        | { system_action | ALL } ]...
