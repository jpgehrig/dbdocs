This illustration shows a sample XStream Out configuration with two outbound servers. The illustration shows two client applications and an Oracle database. The Oracle database includes the following components:

- A redo log that records the changes for the `hr` schema, the `oe.orders` table, and the `oe.order_items` table

- A capture process that captures DML and DDL changes to the `hr` schema, the `oe.orders` table, and the `oe.order_items` table. The capture process converts the changes to logical change records (LCRs) and enqueues the LCRs.

- A queue that stores the LCRs that were captured by the capture process

- An outbound server named `xout` that dequeues LCRs from the queue. One client application receives the dequeued LCRs.

- An outbound server named `xout2` that dequeues LCRs from the queue. A second client application receives the dequeued LCRs.
