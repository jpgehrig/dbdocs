The Quick Configuration: Review OLTP Threshold Settings page is shown.

At the top right are the Cancel, Back, and Finish buttons.

The OLTP Threshold Settings section contains a table.

The column names are Metric Name, AWR Baseline, Threshold Type, Warning Level, and Critical Level. The table has four rows. The values of the rows are the following:

Row 1: Average Active Sessions, SYSTEM_MOVING_WINDOW, Significance Level, Very High (0.99), Extreme (0.9999).

Row 2: Redo Generated (per second), SYSTEM_MOVING_WINDOW, Percentage of Maximum, 100%, 120%.

Row 3: Response Time (per transaction), SYSTEM_MOVING_WINDOW, Significance Level, Very High (0.99), Extreme (0.9999).

Row 4: Session Logical Reads (per transaction), SYSTEM_MOVING_WINDOW, Significance Level, Very High (0.99), None.

The Impact on Existing Thresholds section contains a line of text and a table. The text says: Applying the OLTP threshold settings will also clear the following settings.

The table contains the following columns: Metric Name, AWR Baseline, Threshold Type, Warning Level, Critical Level. The table has one row.

Row 1 has the following values: Number of transactions (per second), BASELINE_TUE_1120, Significance Level, Very High (0.99), Extreme (0.9999).

Row 2 has the following values: "Current Open Cursors Count", null, Fixed Values, 1200, null.

End of description
