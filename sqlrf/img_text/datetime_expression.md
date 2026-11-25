# Description of the illustration datetime_expression.eps

    expr AT
       { LOCAL
       | TIME ZONE { ' [ + | - ] hh:mi'
                   | DBTIMEZONE
                   | 'time_zone_name'
                   | expr
                   }
       }
