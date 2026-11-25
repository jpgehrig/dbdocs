#

    field_list :==

    (column_name { dgen_fld_spec
    | scalar_fld_spec
    | col_obj_fld_spec
    | collection_fld_spec
    | filler_fld_spec }
    )
    [(, column_name { d_gen_fld_spec
    | scalar_fld_spec
    | col_obj_fld_spec
    | collection_fld_spec
    | filler_fld_spec }
    )]...
