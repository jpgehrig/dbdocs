# Description of the illustration dgbkr009.eps

This figure shows a broker configuration consisting of a primary database and a standby database. At the top of the figure, there is a terminal displayed to represent the user interfaces for managing the Data Guard environment: the Data Guard command-line interface (DGMGRL) and Oracle Enterprise Manager.

On the primary database, this figure shows the redo transport services in addition to the following main components: the primary database, Oracle Data Guard monitor (DMON), the online redo log files, and the archived redo log files. The figure also shows standby redo log files in outlined form on the primary side; the standby redo logs are outlined to indicate they are currently inacative but have been configured in preparation for a switchover to the standby role.

The standby database includes the following components: a standby database, log apply services, the Data Guard monitor, archived redo log files, and standby redo log files. The figure also shows the online redo log files in outlined form. Online redo logs are only used if this is a logical standby database. Finally, the figure shows DMON processes on the primary and standby databases communicating with each other over Oracle Net.
