You can configure and manage the IM column store in Oracle Enterprise Manager Cloud Control (Cloud Control).

### A.1 Meeting Prerequisites for Using IM Column Store in Cloud Control

Before you can enable a database to use the IM column store, ensure that the `COMPATIBLE` is set to 12.1.0.0 or higher.

To set the compatibility level, follow these steps:

1.  From the Database Home page in Enterprise Manager, choose Initialization Parameters from the Administration menu to navigate to the Initialization Parameters page.

    You can use this page to set or change the compatibility level.

2.  Search for the `COMPATIBLE` initialization parameter.

    The category for the parameter is Miscellaneous.

3.  Change the value to `12.1.0.0` and click Apply.

    Cloud Control prompts you to restart the database. After the database is restarted, the new value takes effect.

####

To set or change the size of the IM column store, follow these steps:

1.  From the Database Home page in Enterprise Manager, choose Initialization Parameters from the Administration menu to navigate to the Initialization Parameters page.

2.  Search for the parameter `INMEMORY_SIZE`. The category for the parameter is In-Memory.

3.  Change the value and click Apply.

    You can set the value to any value above the minimum size of 100 MB.

    You will then be prompted to restart the database.

### A.2 Using the In-Memory Column Store Central Home Page to Monitor In-Memory Support for Database Objects

Use the In-Memory Column Store Central Home page to monitor In-Memory support for database objects such as tables, indexes, partitions and tablespaces. You can view in-memory functionality for objects and monitor their In-Memory usage statistics.

You can complete the following actions on the In-Memory Column Store Central Home page:

- The In-Memory Object Access Heatmap displays the top 100 objects in the IM column store with their relative sizes and shows you how frequently objects are accessed, represented by different colors. To activate the heat map, you must turn on the option for the Heat Map in the initialization parameter file. Typically, there is a one day wait period before the map is activated. You can use the date selector to pick the date range for objects displayed in the Heat Map. You can also use the slider to control the granularity of the color.

- Use the Configuration section to view the status settings such as In-Memory Query, In-Memory Force, and Default In-Memory Clause. Click Edit to navigate to the Initialization Parameters page where you can change the values and settings displayed in this section. Use the Performance section to view the metrics for Active Sessions.

- Use the Objects Summary section to view the Compression Factor and data about the memory used by the populated objects. The In-Memory Enabled Object Statistics are available in a pop-up window through a drill-down from the View In-Memory Enabled Object Statistics link on the page.

- Use the In-Memory Objects Distribution section to view the distribution on a percentage basis of the various objects used in memory. The section includes a chart showing the distribution of Partitions, Subpartitions, Non-partitioned Tables, and Non-partitioned Materialized Views. The numerical values for each are displayed above the chart.

- Use the In-Memory Objects Search section to search for objects designated for In-Memory use. Click Search after you enter the parameters by which you want to search. The results table shows the Name of each object found along with its Size, Size in Memory, Size on Disk, In-Memory percentage, and its In-Memory parameters. You can also search for accessed objects that are either in-memory or not in-memory. If the Heat Map is enabled, then the Accessed Objects option appears in the drop-down list in the View field of the In-Memory Objects Search box. When you select Accessed Objects, you can filter based on the top 100 objects with access data that are either in-memory or not in-memory. You can select a time range and search for objects within that range. If you select the All Objects In-Memory option, you can view the list of top 100 objects that are in-memory based on their in-memory size.

If you are working in an Oracle RAC environment, you can quickly move between instances by selecting the instance in the Instances selection box above and on the right side of the Heat Map.

### A.3 Specifying In-Memory Details When Creating a Table or Partition

You can specify IM column store details when creating a table or partition.

1.  From the Schema menu, choose Database Objects, then select the Tables option.
2.  Click Create to create a table.
    The Create Table page is shown. Select the In-Memory Column Store tab to specify the in-memory options for the table.
3.  Choose to override the column level in-memory details (if required) in the table below where the columns are specified.
4.  Optionally, you can click on the Partitions tab.
5.  Create table partitions as needed using the wizard.
    To specify IM column store details for a partition, select it from the table in the Partitions tab, and then click Advanced Options.
6.  After entering all necessary IM column store details at the table level, column level, and partitions level, click Show SQL to see the generated SQL. Click OK to create the table.

### A.4 Viewing or Editing IM Column Store Details of a Table

You can view or edit IM column store details of a table.

1.  From the Schema menu, choose Database Objects, and then select the Tables option.
2.  Search for the desired table, and then click View to view its details.
3.  Click Edit to launch the Edit Table page.
    Alternatively, on the Search page, click Edit. Click the In-Memory Column Store tab to specify In-Memory options for the table.
4.  Edit the required details.
5.  Click Apply.

### A.5 Viewing or Editing IM Column Store Details of a Partition

You can view or edit IM column store details of a partition.

1.  From the Schema menu, choose Database Objects, then select the Tables option.
2.  Search for the table that contains the desired partition, select it, and then click View.
3.  Click Edit to launch the Edit Table page.
    Alternatively, on the Table Search page, click Edit.
4.  Click the Partitions tab, and then select the desired partition.
5.  Click Advanced Options.
6.  Edit the required details.
7.  Click OK to return to the Partitions tab.
8.  After making similar changes to all desired partitions of the table, click Apply.

### A.6 Specifying IM Column Store Details During Tablespace Creation

You can specify IM column store details when creating a tablespace.

1.  From the Administration menu, choose Storage, and then select Tablespaces.
2.  Click Create to create a tablespace.
3.  Enter the details that appear on the General tab.
4.  Click the In-Memory Column Store tab.
5.  Enter all required IM column store details for the tablespace.
6.  Click Show SQL.
7.  In the Show SQL page, click Return.
    Another page appears.
8.  Click OK.
9.  Click OK to create the tablespace.

The IM column store settings of a tablespace apply for any new table created in the tablespace. IM column store configuration details must be specified at the individual table level if a table must override the configuration of the tablespace.

### A.7 Viewing and Editing IM Column Store Details of a Tablespace

You can view or edit IM column store details of a tablespace.

1.  From the Administration menu, choose Storage, then select the Tablespaces option.
2.  Search for the desired tablespace, select it, then click View.
3.  Click Edit to launch the Edit Tablespace page, then click the In-Memory Column Store tab.
4.  Edit the required details and click Apply.

### A.8 Specifying IM Column Store Details During Materialized View Creation

You can specify IM column store details when creating a materialized view.

1.  From the Schema menu, choose Materialized Views, then select the Materialized Views option.
2.  Click Create to create a materialized view.
3.  Enter the materialized view name, and specify its query.
4.  Click the In-Memory Column Store tab to specify IM column store options for the materialized view.
5.  After entering all necessary IM column store details, click Show SQL. Click Return from the Show SQL page, and then in the resulting page click OK.
6.  Click OK to create the materialized view.

### A.9 Viewing or Editing IM Column Store Details of a Materialized View

You can view or edit IM column store details of a materialized view.

1.  From the Schema menu, choose Materialized Views, then select the Materialized Views option.
2.  Search for the desired materialized view, and click View to view its details.
3.  Click Edit to launch the Edit Materialized View page.
4.  Click the In-Memory Column Store tab to specify IM column store options for the materialized view.
5.  Edit the required details, and click Apply.
