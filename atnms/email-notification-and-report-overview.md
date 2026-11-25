The following sections provide a brief overview about email notifications and sections of the HTML report output.

- First Email Notification
  After completing health check runs, the daemon emails the assessment report as an HTML attachment to all users that you have specified in the `NOTIFICATION_EMAIL` list.
- What does the Health Check Report Contain?
  Health check reports contain the health status of each system grouped under different sections of the report.
- Subsequent Email Notifications
  For the subsequent health check runs after the first email notification, the daemon emails the summary of differences between the most recent runs.

**Related Topics**

- [Generating a Diff Report](generating-diff-report.md)

**Parent topic:** [Analyzing Risks and Complying with Best Practices](purpose-oracle-orachk-and-oracle-exachk.md)

### 2.2.1 First Email Notification

After completing health check runs, the daemon emails the assessment report as an HTML attachment to all users that you have specified in the `NOTIFICATION_EMAIL` list.

**Parent topic:** Email Notification and Health Check Report Overview

### 2.2.2 What does the Health Check Report Contain?

Health check reports contain the health status of each system grouped under different sections of the report.

The HTML report output contains the following:

- Health score

- Summary of health check runs

- Table of contents

- Controls for report features

- Findings

- Recommendations

Details of the report output are different on each system. The report is dynamic, and therefore the tools display certain sections only if applicable.

#### System Health Score and Summary

System Health Score and Summary report provide:

- A high-level health score based on the number of passed or failed checks

- A summary of health check run includes:
  - Name, for example, Cluster Name

  - Version of the operating system kernel

  - Path, version, name of homes, for example, CRS, DB, and EM Agent

  - Version of the component checked, for example, Exadata

  - Number of nodes checked, for example, database server, storage servers, InfiniBand switches

  - Version of Oracle ORAchk and Oracle EXAchk

  - Name of the collection output

  - Date and time of collection

  - Duration of the check

  - Name of the user who ran the check, for example, `root`

  - How long the check is valid

#### Table of Contents and Report Feature

The Table of Contents section provides links to major sections in the report:

- Database Server

- Storage Server

- InfiniBand Switch

- Cluster Wide

- Maximum Availability Architecture (MAA) Scorecard

- Infrastructure Software and Configuration Summary

- Findings needing further review

- Platinum Certification

- System-wide Automatic Service Request (ASR) health check

- Skipped Checks

- Top 10 Time Consuming Checks

The Report Feature section enables you to:

- Filter checks based on their statuses

- Select the regions

- Expand or collapse all checks

- View check IDs

- Remove findings from the report

- Get a printable view

#### Report Findings

The Report Findings section displays the result of each health check grouped by technology components, such as Database Server, Storage Server, InfiniBand Switch, and Cluster Wide.

Each section shows:

- Check status (`FAIL`, `WARNING`, `INFO`, or `PASS`)

- Type of check

- Check message

- Where the check was run

- Link to expand details for further findings and recommendation

Click View for more information about the health check results and the recommendations.

- What to do to solve the problem

- Where the recommendation applies

- Where the problem does not apply

- Links to relevant documentation or My Oracle Support notes

- Example of data on which the recommendation is based

#### Maximum Availability Architecture (MAA) Score Card

Maximum Availability Architecture (MAA) Score Card displays the recommendations for the software installed on your system.

The details include:

- Outage Type

- Status of the check

- Description of the problem

- Components found

- Host location

- Version of the components compared to the recommended version

- Status based on comparing the version found to the recommended version

**Parent topic:** Email Notification and Health Check Report Overview

### 2.2.3 Subsequent Email Notifications

For the subsequent health check runs after the first email notification, the daemon emails the summary of differences between the most recent runs.

Specify a list of comma-delimited email addresses in the `NOTIFICATION_EMAIL` option.

The email notification contains:

- System Health Score of this run compared to the previous run

- Summary of number of checks that were run and the differences between runs

- Most recent report result as attachment

- Previous report result as attachment

- Diff report as attachment

**Parent topic:** Email Notification and Health Check Report Overview
