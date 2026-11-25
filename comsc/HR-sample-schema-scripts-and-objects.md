This section lists the names of the scripts that create the human resources (`HR`) schema and describes the objects in the schema. Table 4-1 lists the `HR` scripts in alphabetical order, while Table 4-2 lists its objects.

Table 4-1 HR Sample Schema Scripts

| Script Name    | Description                                                                                                      |
|:---------------|:-----------------------------------------------------------------------------------------------------------------|
| `hr_analz.sql` | Collects statistics on the tables in the schema                                                                  |
| `hr_code.sql`  | Creates procedural objects in the schema                                                                         |
| `hr_comnt.sql` | Creates comments for each object in the schema                                                                   |
| `hr_cre.sql`   | Creates the `HR` objects                                                                                         |
| `hr_dn_c.sql`  | Adds the distinguished name column used by Oracle Internet Directory to the `employees` and `departments` tables |
| `hr_dn_d.sql`  | Drops the Oracle Internet Directory distinguished name column from `employees` and `departments`                 |
| `hr_drop.sql`  | Drops schema `HR` and all its objects                                                                            |
| `hr_idx.sql`   | Creates indexes on the `HR` tables                                                                               |
| `hr_main.sql`  | Main script for schema `HR` ; calls other scripts                                                                |
| `hr_popul.sql` | Populates the objects                                                                                            |

Table 4-2 HR Sample Schema Objects

| Object Type | Objects                                                                                                                                                                                                                                                                                                                                          |
|:------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Index       | `COUNTRY_C_ID_PK`, `DEPT_ID_PK`, `DEPT_LOCATION_IX`, `EMP_DEPARTMENT_IX`, `EMP_EMAIL_UK`, `EMP_EMP_ID_PK`, `EMP_JOB_IX`, `EMP_MANAGER_IX`, `EMP_NAME_IX`, `JHIST_DEPARTMENT_IX`, `JHIST_EMPLOYEE_IX`, `JHIST_EMP_ID_ST_DATE_PK`, `JHIST_JOB_IX`, `JOB_ID_PK`, `LOC_CITY_IX`, `LOC_COUNTRY_IX`, `LOC_ID_PK`, `LOC_STATE_PROVINCE_IX`, `REG_ID_PK` |
| Procedure   | `ADD_JOB_HISTORY`, `SECURE_DML`                                                                                                                                                                                                                                                                                                                  |
| Sequence    | `DEPARTMENTS_SEQ`, `EMPLOYEES_SEQ`, `LOCATIONS_SEQ`                                                                                                                                                                                                                                                                                              |
| Table       | `COUNTRIES`, `DEPARTMENTS`, `EMPLOYEES`, `JOBS`, `JOB_HISTORY`, `LOCATIONS`, `REGIONS`                                                                                                                                                                                                                                                           |
| Trigger     | `SECURE_EMPLOYEES`, `UPDATE_JOB_HISTORY`                                                                                                                                                                                                                                                                                                         |
| View        | `EMP_DETAILS_VIEW`                                                                                                                                                                                                                                                                                                                               |
