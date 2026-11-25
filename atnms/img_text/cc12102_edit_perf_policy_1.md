The screenshot shows the Edit Policy page that is used for editing Performance Policies. The top part of the page contains the Policy name (DayTime) and the Policy Description field, an editable text box. The Policy Name is not editable.

Following the Policy Description field is the Performance Definition for Policy:DayTime table, which shows the Performance Objectives for each Performance Class. The descriptive text for this table states "Specify the business ranking and performance objectives for the Performance Classes below. By checking "Measure Only" a Performance Class will be monitored but not managed by QoS Management."

The columns displayed in the table are, from left to right: Performance Class, Rank (editable), Objective Type, Objective Value (secs) (editable), Current Value (sec), and whether or not the objective is marked Measure Only (editable).

The table in the screenshot contains the following rows:

- sales_pc, High, Average Response Time, 0.10000, 0.04213, Measure Only is not selected

- Default_pc, Lowest, Average Response Time, 0.00000, 0.00468, Measure Only is selected

- etl_pc, Medium, Average Response Time, 0.09000, 0.03838, Measure Only is not selected

- salescart_pc, Highest, Average Response Time, 0.10000, 0.06357, Measure Only is not selected

- shipping_pc, High, Average Response Time, 0.09000, 0.05494, Measure Only is not selected

- hr_pc, Medium, Average Response Time, 0.09000, 0.01530, Measure Only is not selected

- erp_pc, High, Average Response Time, 0.07000, 0.02209, Measure Only is not selected

Following the table in the screenshot is the Authorized Actions section and then the Server Pool Directive Override section.

End of description.
