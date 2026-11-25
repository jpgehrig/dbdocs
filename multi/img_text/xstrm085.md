This illustration shows a sample XStream Out configuration that can be configured using the `ADD_OUTBOUND` procedure. The illustration shows a client application and the following three Oracle CDBs:

- The source database contains a redo log that records the changes for the `hr` schema, the `oe.orders` table, and the `oe.order_items` table.

- The capture database can be the source database, the outbound server database, or a third database. The capture database contains the following components:

  - A capture process capturing changes from the redo log of the source database. If the capture database and the source database are the same, then a local capture process captures changes in the redo log at the source database. If the capture database is the destination database or a third database, then the source database redo log is shipped to the capture database, and a downstream capture process captures changes in this redo log.

  - The capture process converts the changes to logical change records (LCRs) and enqueues the LCRs.

  - If the capture database and the outbound server database are different databases, then a propagation propagates the LCRs to a queue at the outbound server database. If the capture database and outbound server database are the same, then the propagation is not needed.

- The outbound server database contains the following:

  - The queue that contains LCRs that were captured by the capture process.

  - An outbound server named `xout` that dequeues LCRs from the queue. The client application receives the dequeued LCRs.
