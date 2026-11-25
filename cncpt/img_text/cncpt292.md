# Description of the illustration cncpt292.eps

This figure shows the tables in the HR schema and the columns in each table, as well as dependencies between the tables.

The job_history has columns employee_id (primary key), start_date (primary key), end_date, job_id, and department_id. Each job history record must be associated with one employee in the employees table.

The jobs table has the columns job_id (primary key), job_title, min_salary, and max_salary. Each job may be related to one or more employees in the employees table.

The departments table has columns department_id (the primary key), department_name, manager_id, and location_id. Each department must be related to one or more employees in the employee table and must be related to one location in the locations table.

The employees table has columns employee_id (primary key), first_name, last_name, email, phone_number, hire_date, job_id, salary, commission_pct, manager_id, and department_id. Each employee must be related to one department in the departments table and one job in the jobs table, and may be related to one or more records in the job_history table.

The locations table has columns location_id (primary key), street_address, postal_code, city, state_province, and country_id. Each location may be associated with one or more departments and must be associated with one country.

The countries table has columns country_id (primary key), country_name, and region_id. Each country may be related to one or more locations and must be associated with one region.

The regions table has columns region_id (primary key) and region_name. Each region may be associated with one or more countries.
