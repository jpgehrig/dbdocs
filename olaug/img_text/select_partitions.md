This screen capture shows the Partitioning subpage of the property sheet for the Units Cube cube. At the top of the property sheet are the tabs General, Aggregation, Partitioning, Storage, and Materialized Views.

The Partitioning subpages has the Partition Cube option, which is selected. The subpage has the tabs Select Partitions and Partition Member Analysis. Select Partitions subpage is selected.

On the Select Partitions subpage is the text, "Select one dimension and one or more levels to use for partitioning. Each dimension member at the selected level is stored in a separate partition with its descendants. Click Help for more information." From the Dimension list, Time is selected. The Aggregation Hierarchies lists display the hierarchies and levels for the Time dimension. The hierarchies are Calendar and Fiscal.

The options for the Calendar hierarchy levels are the following:

TOTAL: 1 members

CALENDAR_YEAR: 10 members

CALENDAR_QUARTER: 40 members

MONTH: 120 members

The options for the Calendar hierarchy levels are the following:

TOTAL: 1 members

FISCAL_YEAR: 11 members

FISCAL_QUARTER: 40 members

MONTH: 120 members

The CALENDAR_QUARTER option is selected to be partitioned and MONTH in the CALENDAR hierarchy is designated to be in the partitions.

Above the Aggregation Hierarchies options are the Order Hierarchies and Clear Selections buttons. Below the Aggregation Hierarchies options is a table. The columns of the table are Partition Order, Partition Name, Partition Includes, and Precompute. The table has one row, which has the following values: 1, CALENDAR.CALENDAR_QUARTER, CALENDAR_QUARTER, MONTH, 40.

Below the table is the Automatically Manage Partition Order option, which is selected.

Below that option are the Help, Apply, and Revert buttons.
