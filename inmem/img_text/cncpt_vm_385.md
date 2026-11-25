#

This graphic depicts the SGA. The SGA contains the Database Buffer Cache and the In-Memory Column Store (IM column store). In the IM column store are columns from three tables: products, customers, and sales. Each table is divided into IMCUs. There are 6 total IMCUs, labeled IMCU 1 through IMCU 6.

Below the SGA are two tablespaces: USERS and FS_TBS. The USERS tablespace contains segments for customers, products, and sales. FS_TBS contains IMCU 1 through IMCU 6. A double-headed arrow is between the IM column store and FS_TBS.
