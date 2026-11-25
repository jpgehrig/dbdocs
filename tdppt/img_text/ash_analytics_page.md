The ASH Analytics page is shown.

At the top of the page are the following elements:

- Save icon

- Page Refreshed field showing the time at which the page was last refreshed

- Auto Refresh list with 15 seconds selected

Below those elements is a stacked area chart that shows the average active sessions in a specified time period. The units of the y-axis of the chart are average active sessions, which range from 0 to 1.2. The units of the x-axis are times of the day, shown in 5-minute intervals. The marked times range from 12:55 p.m. to 1:50 p.m. A shaded slider area covers the time from about 1:31to 1:37.

Above the chart are the following options: Hour (selected), Day, Week, Month, Calendar, Custom.

Below the chart is the Filters list with the value None.

Below that are the Activity and Load Map tabs. The Activity tab is selected.

At the top of the Activity section is a list of activities with Wait Class selected. Next to that list are the Show options: Total Activity and CPU Cores. Both options are selected.

A stacked area chart shows details about the activities for the selected time period.

The units of the x-axis of the chart are times of the day, shown in 30-second intervals. The x-coordinates shown range from 1:30:45 p.m. to 1:35:15 p.m. The units of the y-axis are average active sessions. The y-coordinates shown range from 0 to about 3.4. A line at the 2 mark indicates the number of CPU Cores.

A legend to the right of the chart shows the types of events that could appear in the chart. The types of events are the following: Other, Configuration, Commit, Concurrency, System I/O, User I/O, CPU.

The number of average active sessions is mostly between 1 and 1.2 with a sharp spike up to 3.4 at about 1:33:35. The activity is predominately CPU with some configuration and commit. The spike shows CPU, system I/O, concurrency, commit, configuration, and other activity.

The page has two tables that show more information about the dimension selected for the Activities chart. Above each table is a dimensions list. For the table on the left, SQL ID is selected so the table shows SQL ID activity by wait class. For the table on the right, User Session is selected so the table shows User Session activity by wait class.

The columns of the table on the left are Select, SQL ID, and Activity (Average Active Sessions). The values in the Select column rows are check boxes, and in the Activity (Average Active Sessions) column rows the values are horizontal bar charts and associated numbers. The bar chart shows the type and relative amount of activity. Two rows are visible in the table. The values of the rows are the following.

Row 1: Not selected, 5a457c2y2wwm3, the bar chart shows about 80% CPU and about 20% configuration activity and the number is 1.

Row 2: Not selected, 0s8qqvi1hob34, bar, \<.01, the bar chart shows about 60% CPU and about 40% configuration activity.

The columns of the table on the right are User Session and Activity (Average Active Sessions). The values in the Activity (Average Active Sessions) column rows are horizontal bar charts and associated numbers. Two rows are visible in the table. The values of the rows are the following.

Row 1: 1:12,4923, the bar chart shows about 80% CPU and about 20% configuration activity and the number is 1.

Row 2: 1:88.1, the bar chart shows about 100% CPU activity and the number is .03.

End of description.
