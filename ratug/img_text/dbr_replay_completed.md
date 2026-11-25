# Description of the illustration dbr_replay_completed.gif

There are three tabs on this page: Home, Reports, and Review. The Home tab is open.

The Replay Summary section appears in the upper left corner, and values are shown for the following read-only fields:

Database Target

Database Name

Database Version

Status

Owner

Replay Duration (hh:mm:ss)

Replay Start Time

Replay End Time

Replay Error Code

Replay Error Message

SQL Tuning Set Name

Replay Job Name

Replay Host

Replay Directory Path

The Replay Divergence Summary section appears in the lower left corner. In this section, a table appears with the Divergence Type, Count, and Divergence Percentage columns. There are six rows with the following divergence types:

Session Failures During Replay

Errors No Longer Seen During Replay

New Errors Seen During Replay

Errors Mutated During Replay

DMLs with Different Number of Replays

SELECTS with Different Number of Replays

There are values for each row for the Count column and Divergence Percentage column.

The Replay Progress section appears in the upper right corner. It contains the Average Active Calls tab, which is open, and the User Calls tab.

The Average Active Sessions tab contains a chart. The chart has a y-axis labeled Active Sessions The y-axis values range from 0.0 to 3.0. The chart has an x-axis labeled Elapsed Time (Minutes). The x-axis values range from 0.0 to 50.0. The chart shows values for Other Activity, CAP_EAST, and CAP_WEST.

The Replay Statistics section appears in the lower right corner, and contains the Database Time (Minutes) and User Calls (Thousands) vertical charts for Replay and Capture. Values are shown for CAP_EAST, CAP_WEST, and BB_TIME_SHIFT.

End of description.
