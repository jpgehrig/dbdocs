This screenshot shows the Performance Finding Details: Undersized Buffer Cache page.

Under the page title are the following label-value pairs:

- Finding: he buffer cache was undersized causing significant additional read I/O.

  Associated with the finding is the Finding History button.

- Impact (Active Sessions): .01

- Impact (%): 2.1

- Period Start Time: Jan 20, 2012 4:00:40 PM PST

- Period Duration (minutes): 29.5

- Filtered: No

  Associated with the filtered value is the Filters button.

In the Recommendations section are the links Show All Details and Hide All Details. A table contains the following columns: Details, Category, and Benefit (%).

Underneath the row of links is a table. The table contains the following columns: Details, Category, and Benefit (%). Values in the Details column are displayed as a collapsible navigation tree. Values in the Benefit column are displayed as a horizontal bar chart with an associated number.

The table has one row. The values of row are: Hide, DB Configuration, and 2.1. Below that row is the following additional information about the finding: Action, "Increase the buffer cache size by setting the value of parameter DB_CACHE_SIZE to 160M." After the text are the following buttons: Implement, and Filters.

The Additional Information section contains the following message: The value of parameter "db_cache_size" was "96 M" during the analysis period.

In the Findings Path section, the Expand All and Collapse All links appear in the upper left. The table has the following columns: Findings, Impact (%), and Additional Information. The first row has the values: "The buffer cache was undersized causing significant additional read I/O," 2.1 (shown as a bar chart), and an Additional Information link. The second row has the values: "Wait class 'User I/O' was consuming significant database time," 2.1 (shown as a bar chart with an associated number), and null.

End of description.
