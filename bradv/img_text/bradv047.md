# Description of the illustration bradv047.eps

This graphic illustrates backup-based duplication with a target connection. The RMAN client is at the bottom of the graphic. At the top-right is the Duplicate Database, which resides on the Destination Host. The rectangle to the left of the duplicate database is labeled Auxiliary Instance. Below the Duplicate Database are rectangles that are labeled RMAN Backups. The Duplicate Database is connected through an arrow to the RMAN Backups, displayed below the database. At the top-left is the Source Database, which resides on the source Host. The rectangle labeled Source Instance is to the right of the source database.

An arrow from the RMAN client to the Duplicate Database, labelled Connect Auxiliary, indicates that RMAN connects to the duplicate database AS AUXILIARY. The arrow from the RMAN client to the Source Database, labelled Connect Target, indicates that RMAN connects to the recovery catalog database AS TARGET.
