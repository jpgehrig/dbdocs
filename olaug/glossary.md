### additive

Describes a measure or fact that can be summarized through addition, such as a `SUM` function. An additive measure is the most common type. Examples include sales, cost, and profit.

Contrast with nonadditive.

### aggregation

The process of consolidating data values into a single value. For example, sales data could be collected on a daily basis and then be aggregated to the week level, the week data could be aggregated to the month level, and so on. The data can then be referred to as aggregate data.

The term aggregation is often used interchangeably with summarization, and aggregate data is used interchangeably with summary data. However, there are a wide range of aggregation methods available in addition to `SUM`.

### analytic workspace

A container for storing related dimensional objects, such as dimensions and cubes. An analytic workspace is stored in a relational table.

See also cube, cube dimension.

### ancestor

A dimension member at a higher level of aggregation than a particular member. For example, in a Time dimension, the year 2007 is the ancestor of the day 06-July-07. The member immediately above is the parent. In a dimension hierarchy, the data value of the ancestor is the aggregated value of the data values of its descendants.

Contrast with descendant. See also hierarchy, level, parent.

### attribute

A database object related to an OLAP cube dimension. An attribute stores descriptive characteristics for all dimension members, or members of a particular hierarchy, or only members at a particular level of a hierarchy.

When the values of an attribute are unique, they provide supplementary information that can be used for display (such as a descriptive name) or in analysis (such as the number of days in a time period). When the values of an attribute apply to a group of dimension members, they enable users to select data based on like characteristics. For example, in a database representing footwear, you might use a color attribute to select all boots, sneakers, and slippers of the same color.

See also cube dimension.

### base level data

See detail data.

### base measure

See measure.

### calculated measure

A stored expression that executes in response to a query. For example, a calculated measure might generate the difference in costs from the prior period by using the `LAG_VARIANCE` function on the `COSTS` measure. Another calculated measure might calculate profits by subtracting the `COSTS` measure from the `SALES` measure. The expression resolves only the values requested by the query.

See also expression, measure.

### cell

A single data value of an expression. In a dimensioned expression, a cell is identified by one value from each of the dimensions of the expression. For example, if you have a measure with the dimensions `MONTH` and `CUSTOMER`, then each combination of a month and a customer identifies a separate cell of that measure.

See also cube dimension.

### child

A dimension member that is part of a more aggregate member in a hierarchy. For example, in a Time dimension, the month Jan-06 might be the child of the quarter Q1-2006. A dimension member can be the child of a different parent in each hierarchy.

Contrast with parent. See also descendant, hierarchy.

### composite

A compact format for storing sparse multidimensional data. Oracle OLAP provides two types of composites: a compressed composite for extremely sparse data, and a regular composite for moderately sparse data.

See also dimension, sparsity.

### compressed cube

A cube with very sparse data that is stored in a compressed composite.

See also composite.

### compression

See compressed cube.

### consistent solve specification

See solve specification.

### cube

An organization of measures with identical dimensions and other shared characteristics. The edges of the cube contain the dimension members, and the body of the cube contains the data values. For example, sales data can be organized into a cube whose edges contain values from the Time, Product, and Customer dimensions and whose body contains Volume Sales and Dollar Sales data.

### cube dimension

A cube dimension is a dimensional object that stores a list of values. It is an index for identifying the values of a measure. For example, if Sales data has a separate sales figure for each month, then the data has a Time dimension that contains month values, which organize the data by month.

In the context of multidimensional analysis, a cube dimension is called a dimension.

See also dimension.

### cube materialized view

A cube that has been enhanced with materialized view capabilities. A cube materialized view can be incrementally refreshed through the Oracle Database materialized view subsystem, and it can serve as a target for transparent rewrite of queries against the source tables.

Also called a cube-organized materialized view.

### cube script

A sequence of steps that prepare the data for querying, such as loading and aggregating data.

### cube view

A relational view of the data stored in a cube, which can be queried by SQL. It contains columns for the dimensions, measures, and calculated measures of the cube.

### custom measure

See calculated measure.

### custom member

A dimension member whose data is calculated from the values of other members of the same dimension using the rules defined in a model.

See model.

### data security role

A group of users and database roles that is defined just for use in managing OLAP security policies.

### data source

A relational table, view, synonym, or other database object that provides detail data for cubes and cube dimensions.

### data warehouse

A database designed for query and analysis rather than transaction processing. A data warehouse usually contains historical data that is derived from transaction data, but it can include data from other sources. It separates analysis workload from transaction workload and enables a business to consolidate data from several sources.

### denormalized

Permit redundancy in a table. Contrast with normalize.

### derived measure

See calculated measure.

### descendant

A dimension member at a lower level of aggregation than a particular member. For example, in a Time dimension, the day 06-July-07 is the descendant of year 2007. The member immediately below is the child. In a dimension hierarchy, the data values of the descendants roll up into the data values of the ancestors.

Contrast with ancestor. See also aggregation, child, hierarchy, level.

### detail data

Data at the lowest level, which is acquired from another source.

Contrast with aggregation.

### dimension

A structure that categorizes data. Among the most common dimensions for sales-oriented data are Time, Geography, and Product. Most dimensions have hierarchies and levels.

In a cube, a dimension is a list of values at all levels of aggregation.

In a relational table, a dimension is a type of object that defines hierarchical (parent-child) relationships between pairs of column sets.

See also cube dimension, hierarchy, measure dimension.

### dimension key

See dimension member.

### dimension member

One element in the list that composes a cube dimension. For example, a Time dimension might have dimension members for days, months, quarters, and years.

### dimension table

A relational table that stores all or part of the values for a dimension in a star or snowflake schema. Dimension tables typically contain columns for the dimension keys, levels, and attributes.

### dimension value

See dimension member.

### dimension view

A relational view of a cube dimension that provides information about all members of all hierarchies. It includes columns for the dimension keys, level, and attributes.

See also cube dimension, hierarchy view.

### drill

To navigate from one item to a set of related items. Drilling typically involves navigating up and down through the levels in a hierarchy.

Drilling down expands the view to include child values that are associated with parent values in the hierarchy.

Drilling up collapses the list of descendant values that are associated with a parent value in the hierarchy.

### EIF file

A specially formatted file for transferring data between analytic workspaces, or for storing versions of an analytic workspace (all of it or selected objects) outside the database.

### embedded total

A list of dimension members at all levels of a hierarchy, such that the aggregate members (totals and subtotals) are interspersed with the detail members. For example, a Time dimension might contain dimension members for days, months, quarters, and years.

### expression

A combination of one or more values (typically provided by a measure or a calculated measure), operators, and functions that evaluates to a value. An expression generally assumes the data type of its components.

The following are examples of expressions, where `SALES` is a measure: `SALES`, `SALES*1.05`, `TRUNC(SALES)`.

### fact

See measure.

### fact table

A table in a star schema that contains factual data. A fact table typically has two types of columns: those that contain facts and those that are foreign keys to dimension tables. The primary key of a fact table is usually a composite key that is made up of all of its foreign keys.

A fact table might contain either detail facts or aggregated facts. Fact tables that contain aggregated facts are typically called summary tables or materialized views. A fact table usually contains facts with the same level of aggregation.

See also materialized view.

### hierarchy

A way to organize data at different levels of aggregation. Hierarchies are used to define data aggregation; for example, in a Time dimension, a hierarchy might be used to aggregate data from days to months to quarters to years. Hierarchies are also used to define a navigational drill path.

In a relational table, hierarchies can be defined as part of a dimension object.

See also level-based hierarchy, ragged hierarchy, skip-level hierarchy, value-based hierarchy.

### hierarchy view

A relational view of a cube dimension that provides information about the members that belong to a particular hierarchy. It includes columns for the dimension keys, parents, levels of the hierarchy, and attributes.

See also cube dimension, dimension view.

### key

A column or set of columns included in the definition of certain types of integrity constraints. Keys describe the relationships between the different tables and columns of a relational database.

See also dimension member.

### leaf data

See detail data.

### level

A named position in a hierarchy. For example, a Time dimension might have a hierarchy that represents data at the month, quarter, and year levels. The levels might be named Month, Quarter, and Year. The names provide an easy way to reference a group of dimension members at the same distance from the base.

### level-based hierarchy

A hierarchy composed of levels. For example, Time is always level based with levels such as Month, Quarter, and Year. Most hierarchies are level based.

See also value-based hierarchy.

### mapping

The definition of the relationship and data flow between source and target objects. For example, the metadata for a cube includes the mappings between each measure and the columns of a fact table or view.

### materialized view

A database object that provides access to aggregate data and can be recognized by the automatic refresh and the query rewrite subsystems.

See also cube materialized view.

### measure

Data that represents a business measure, such as sales or cost data. You can select, display, and analyze the data in a measure. The terms measure and fact are synonymous; measure is more commonly used in a multidimensional environment and fact is more commonly used in a relational environment.

Measures are dimensional objects that store data, such as Volume Sales and Dollar Sales. Measures belong to a cube.

See also calculated measure, fact, cube.

### measure dimension

A dimension that has measures as dimension members.

### measure folder

A database object that organizes and label groups of measures. Users may have access to several schemas with measures named Sales or Costs, and measure folders provide a way to differentiate among them.

### model

A set of interrelated equations specified using the members of a particular dimension. Line item dimensions often use models to calculate the values of dimension members.

See also custom member. Contrast with calculated measure.

### NA value

A special data value that indicates that data is "not available" (`NA`) or null. It is the value of any cell to which a specific data value has not been assigned or for which data cannot be calculated.

See also cell, sparsity.

### nonadditive

Describes a measure or fact that cannot be summarized through addition, such as Unit Price. Maximum is an example of a nonadditive aggregation method.

Contrast with additive.

### normalize

In a relational database, the process of removing redundancy in data by separating the data into multiple tables. Contrast with denormalized.

### OLAP

Online Analytical Processing. OLAP functionality is characterized by dynamic, dimensional analysis of historical data, which supports activities such as the following:

- Calculating across dimensions and through hierarchies

- Analyzing trends

- Drilling up and down through hierarchies

- Rotating to change the dimensional orientation

Contrast with OLTP.

### OLAP DML

A set of commands, functions, and options used to manage dimensional data stored in analytic workspaces within Oracle Database.

Analytic Workspace Manager, the OLAP expression syntax, the OLAP Java API, and various applications and PL/SQL packages enable users to access dimensional data without using the OLAP DML directly, but those tools use the OLAP DML to accomplish the desired tasks.

The OLAP Data Manipulation Language (DML) operates exclusively within analytic workspaces, whose primary data structures are dimensions, variables, formulas, relations, and valuesets. These dimensional objects in analytic workspaces support the high-level dimensional objects in the database, such as cubes, cube dimensions, measures, attributes, and hierarchies.

Contrast with OLAP expression syntax.

### OLAP expression syntax

An extension of the SQL syntax that is used to manipulate the data stored in dimensional database objects such as cubes, cube dimensions, attributes, and measures.

Contrast with OLAP DML.

### OLTP

Online Transaction Processing. OLTP systems are optimized for fast and reliable transaction handling. Compared to data analysis systems, most OLTP interactions involve a relatively small number of rows, but a larger group of tables.

Contrast with OLAP.

### on the fly

Calculated at run time as needed in response to a specific query. In a cube, calculated measures and custom members are typically calculated as needed. Aggregate data can be precomputed, calculated as needed, or a combination of the two methods.

Contrast with precompute.

### override solve specification

See solve specification.

### page

A unit for swapping data in and out of memory.

Also called a block.

### page space

A grouping of related data pages.

### parent

A dimension member immediately above a particular member in a hierarchy. In a dimension hierarchy, the data value of the parent is the aggregated total of the data values of its children.

Contrast with child. See also hierarchy, level.

### parent-child relation

A one-to-many relationship between one parent and one or more children in a hierarchical dimension. For example, New York (at the state level) might be the parent of Albany, Buffalo, Poughkeepsie, and Rochester (at the city level).

See also child, parent.

### precalculate

See precompute.

### precompute

Calculate and store as a data maintenance procedure. In a cube, aggregate data can be precomputed, calculated as needed, or a combination of the two methods.

Contrast with on the fly.

### ragged hierarchy

A hierarchy that contains at least one member with a different base level, creating a "ragged" base level for the hierarchy. Organization dimensions are frequently ragged.

### refresh

Load new and changed values from the source tables and recompute the aggregate values.

### security role

See data security role.

### skip-level hierarchy

A hierarchy that contains at least one member whose parents are multiple levels above it, creating a hole in the hierarchy. For example, in a Geography dimension with levels for City, State, and Country, Washington D.C. is a city that does not have a State value; its parent is United States at the Country level.

### snowflake schema

A type of star schema in which the dimension tables are partly or fully normalized.

See also normalize, star schema.

### solve specification

The aggregation method for each dimension of the cube.

### solved data

A result set in which all derived data has been calculated. Data fetched from a cube is always fully solved, because all of the data in the result set is calculated before it is returned to the SQL-based application. The result set from the cube is the same whether the data was precomputed or calculated as needed.

See also on the fly, precompute.

### source

See data source.

### sparsity

A concept that refers to multidimensional data in which a relatively high percentage of the combinations of dimension values do not contain actual data.

There are two types of sparsity:

- Controlled sparsity occurs when a range of values of one or more dimensions has no data; for example, a new measure dimensioned by Month for which you do not have data for past months. The cells exist because you have past months in the Month dimension, but the cells are empty.

- Random sparsity occurs when nulls are scattered throughout a measure, usually because some combinations of dimension members never have any data. For example, a district might only sell certain products and never have sales data for the other products.

Some dimensions may be sparse while others are dense. For example, every time period may have at least one data value across the other dimensions, making Time a dense dimension. However, some products may not be sold in some cities, and may not be available anywhere for some time periods; both Product and Geography may be sparse dimensions.

See also composite.

### star query

A join between a fact table and several dimension tables. Each dimension table is joined to the fact table using a primary key to foreign key join, but the dimension tables are not joined to each other.

### star schema

A relational schema whose design represents a dimensional data model. The star schema consists of one or more fact tables and one or more dimension tables that are related through foreign keys.

See also snowflake schema.

### status

The list of currently accessible values for a given dimension. The status of a dimension persists within a particular session, and does not change until it is changed deliberately. When an analytic workspace is first attached to a session, all members are in status.

See also cube dimension, dimension member.

### summary

See aggregation.

### update window

The length of time available for loading data into a database.

### value-based hierarchy

A hierarchy defined only by the parent-child relationships among dimension members. The dimension members at a particular distance from the base level do not form a meaningful group for analysis, so the levels are not named. For example, an employee dimension might have a parent-child relation that identifies each employee's supervisor. However, levels that group first-, second-, and third-level supervisors and so forth may not be meaningful for analysis.

See also hierarchy, level-based hierarchy.
