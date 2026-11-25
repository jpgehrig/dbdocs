## Review Deprecated and Desupported Features

Before you upgrade, check to see if deprecated or desupported features require attention in your upgrade plan.

Every release, Oracle modifies or removes support for features, views, and parameters, so that Oracle can focus on improving core manageability and functionality of other features in the database. For that reason, as part of your upgrade planning, Oracle recommends that you review the list of features listed as deprecated or desupported in a new release, and determine if these changes are of concern for your applications.

There are two categories of features scheduled for removal:

- **Deprecated** features are features that are no longer being enhanced, but are still supported for the full life of this release of Oracle Database.

- **Desupported** features are features that are no longer supported by fixing bugs related to that feature. Often, Oracle can choose to remove the code required to use the feature. A deprecated feature can be desupported in the next Oracle Database release.

If you see that a feature is deprecated, then Oracle strongly recommends that you stop using that feature as soon as it is practicable for you to do so. Start planning your migration away from deprecated features at the time that they are deprecated.

**Parent topic:** [Tasks to Prepare for Oracle Database Upgrades](tasks-to-prepare-for-oracle-database-upgrades.md)
