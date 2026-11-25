## 4.280 DBA_EPG_DAD_AUTHORIZATION

`DBA_EPG_DAD_AUTHORIZATION` describes the DADs that are authorized to use different user's privileges.

### Related View

`USER_EPG_DAD_AUTHORIZATION` describes the DADs that are authorized to use the user's privileges. This view does not display the `USERNAME` column.

| Column     | Datatype        | NULL     | Description                                                    |
|:-----------|:----------------|:---------|:---------------------------------------------------------------|
| `DAD_NAME` | `VARCHAR2(64)`  | NOT NULL | Name of DAD                                                    |
| `USERNAME` | `VARCHAR2(128)` | NOT NULL | Name of the user whose privileges the DAD is authorized to use |

**See Also:**

"[USER_EPG_DAD_AUTHORIZATION](USER_EPG_DAD_AUTHORIZATION.md)"
