Creating a Calculated Measure: This screen capture shows the General subpage of the Create Calculated Measure dialog box. The following values are shown:

- Name: UNITS_PP

- Short Label: Units Pp

- Long Label: Units Prior Period

- Description: Units Prior Period

- Calculation type: Prior Period

- Calculation: Period period for measure UNITS in TIME dimension and TIME.CALENDAR hierarchy 1 period ago

- Expression: LAG(UNITS_CUBE.UNITS, 1) OVER HIERARCHY(TIME.CALENDAR)

The Advanced option is selected.

Below that option are tabs for the References, Dependencies, and Expressions subpages. The References subpage is selected. The page has a table that has the following columns: Create, Name, Short Label, Long Label, Description, Expression.

The table has one row. The row has the following values: null, UNITS, Units, Units, Units, null.
