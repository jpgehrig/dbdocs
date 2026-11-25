This illustration shows a sample XStream Out configuration that can be configured using the `CREATE_OUTBOUND` procedure. The illustration shows a client application and an Oracle database. The Oracle database includes the following components:

- A redo log that records the changes for the `hr` schema, the `oe.orders` table, and the `oe.order_items` table

- A capture process that captures DML and DDL changes to the `hr` schema, the `oe.orders` table, and the `oe.order_items` table. The capture process converts the changes to logical change records (LCRs) and enqueues the LCRs.

- A queue that stores the LCRs that were captured by the capture process

- An outbound server named `xout` that dequeues LCRs from the queue. The client application receives the dequeued LCRs.
