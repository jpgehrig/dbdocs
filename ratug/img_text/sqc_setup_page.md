# Description of the illustration sqc_setup_page.png

The SQL Performance Analyzer Setup page is shown.

The top of the page includes the text "This page is used to configure the settings for the 'validate with SQL Performance Analyzer' option available from certain database management pages. These options are used to validate the performance of the database after changing database settings."

Below the text, the left side of the page includes options that you can select, and the right side of the page includes a text box that describes the options.

The left side of the page includes 10 fields. From top to bottom, the fields are:

- SQL Tuning Set: A Search icon is available for this field, which lets you choose a previously defined SQL tuning set. In the screenshot, the SYSTEM.RUNLOAD value appears in the field.

- Trial Mode: You can choose either the Optimal (Hybrid), Test Execute, or Explain Plan option for this field. In the screenshot, the Optimal (Hybrid) option is selected.

- Per-SQL Time Limit (Seconds): In the screenshot, a value of 300 appears in the field.

- Execute Full DML: You can choose either the Yes or No option. In the screenshot, the No option is selected.

- Workload Impact Threshold(%): A value between 0 and 100 can be entered In this field. In the screenshot, a value of 1 has been selected.

- SQL Impact Threshold(%): A value between 0 and 100 can be entered In this field. In the screenshot, a value of 1 has been selected.

- Disable Multiple Executions: You can choose either the Yes or No option. In the screenshot, the Yes option is selected.

- Comparison Metric: You can choose different comparison metrics for this field. In the screenshot, the Elapsed Time metric has been selected.

- Use Resource Consumer Group: You can choose either the Yes or No option. In the screenshot, the No option is selected.

- Resource Consumer Group: A Search icon is available for this field, which gives you the option of choosing a previously defined resource consumer group. In the screenshot, a resource consumer group is not selected.

After all the fields on the left side of the page, the Save button appears.

The right side of the page includes a text box that includes descriptions of some of the fields on the left side of the page. The text box includes three sections, which are the Trial Mode section, the Workload Impact Threshold(%), SQL Impact Threshold(%) section, and the Disable Multiple Executions section.

The Trial Mode section includes text descriptions of these options:

- Optimal (Hybrid): This is the recommended mode. It finds SQLs with plan changes first by generating plan, then test-executes SQL statements with plan changes.

- Test Execute: Test-execute every SQL statement and collect its execution plans and executions statistics.

- Explain Plan: Generate explain plan for every statement in the SQL workload.

The Workload Impact Threshold(%), SQL Impact Threshold(%) section includes the text "These settings control the threshold where SQL is reported as having regressed or improved. The Workload Impact Threshold is the percent impact of the chosen metric on the entire workload. The SQL Impact Threshold is the percent impact of the chosen metric on the individual SQL statement. Only statements that exceed both percentages will be reported as regressed or improved."

The Disable Multiple Executions section includes the text "By default, SPA executes short running SQL multiple times to eliminate buffer warm up effects. This option enables those multiple executions."

End of description.
