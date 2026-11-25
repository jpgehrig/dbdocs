# Description of the illustration bradv045a.gif

This graphic illustrates active database duplication. The RMAN client is at the bottom of the graphic. At the top-right is the Duplicate Database, which resides on the Destination Host. The rectangle to the left of the duplicate database is labeled Auxiliary Instance. At the top-left is the Source Database, which resides on the Source Host. The rectangle labeled Source Instance is to the right of the source database.

An arrow from the RMAN client to the Duplicate Database, labelled Connect Auxiliary, indicates that RMAN connects to the duplicate database AS AUXILIARY. The arrow from the RMAN client to the Source Database, labelled Connect Target, indicates that RMAN connects to the duplicate database AS TARGET. A dotted-line arrow from the Auxiliary Instance to the Source Instance is labeled pull-based active database duplication.
