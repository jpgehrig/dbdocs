# Description of the illustration ilm_inmemory_policy.eps

    { SET INMEMORY [ inmemory_attributes ]
    | MODIFY INMEMORY inmemory_memcompress
    | NO INMEMORY
    }
    [ SEGMENT ]
    { AFTER ilm_time_period OF { NO ACCESS | NO MODIFICATION | CREATION }
            | ON function_name
            }
