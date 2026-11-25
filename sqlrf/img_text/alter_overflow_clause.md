# Description of the illustration alter_overflow_clause.eps

    { add_overflow_clause
    | OVERFLOW
         { segment_attributes_clause
         | allocate_extent_clause
         | shrink_clause
         | deallocate_unused_clause
         }...
    }
