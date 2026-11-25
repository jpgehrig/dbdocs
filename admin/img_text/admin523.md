# Description of the illustration admin523.eps

This illustration shows two databases: Database I is the master database and Database II is the materialized view database. This illustration shows two methods for creating materialized views: Method A creates a complex materialized view by joining two master tables while Method B creates two simple materialized views with each one based on only one master table.

The complex materialized view must perform slower complete refreshes while the simple materialized views can perform quicker fast refreshes. However, queries on the data in the complex materialized view return faster than queries that must join the two simple materialized views.
