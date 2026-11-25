Two messages are linked by arrows to illustrate the conversion process. The Advanced Queuing Message consists of an AQ Property and an AQ Payload. The Messaging Gateway Message consists of an AQ Property and a Canonical Type.

An arrow labeled Outbound Propagation points from the AQ Property of the Advanced Queuing Message to the AQ Property of the Messaging Gateway Message. Another Outbound Propagation arrow points from the AQ Payload of the Advanced Queuing Message to the Canonical Type of the Messaging Gateway Message. Arrows labeled Inbound Propagation form the same links, but pointing in the other direction.

Optional user-supplied Transformation Functions, to convert between message types, are represented as detours on the two arrows linking message payloads.
