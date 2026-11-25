# Description of the illustration dgbkr003.eps

This figure emphasizes the discussion in the surrounding text that describes the DMON process as one of many Oracle background processes. The top half of the figure shows a primary database on which the Oracle database is interacting with the DMON process and many other background processes such as the Recoverer (RECO), Process Monitor (PMON), System Monitor (SMON), Database Writer (DBW0), Log Writer (LGWR), and the Archiver (ARC0). An elliptical series of dots indicates that the number of processes continues beyond the ones shown in this figure.

The bottom half of the figure represents the standby database as a mirror image of the primary database, showing that there is a DMON process on the standby database along with a series of Oracle database processes as shown on the primary database.

The figure also shows that two-way communication occurs between the DMON processes on the primary and standby databases over the Oracle Net communication channel.
