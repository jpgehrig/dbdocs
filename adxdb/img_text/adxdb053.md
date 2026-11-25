The figure shows a database with table `HR.employees` at the left, a DBUri at the right, and an XML visualization between them. The XML visualization is shown projecting from table `HR.employees`. An arrow points from the DBUri to the XML visualization.

The database table shows columns `employee_id` and `last_name`. Column `employee_id` has entries `200` and `177`. Column `last_name` has entries `Whalen` and `Livingston`.

The DBUri is this: `/oradb/HR/EMPLOYEES/ROW[EMPLOYEE_ID=200]/LAST_NAME`

The XML visualization is this:

    <HR>
     <ROW>
      <EMPLOYEE_ID>
        200
      </EMPLOYEE_ID>
     </ROW>
    </HR>
