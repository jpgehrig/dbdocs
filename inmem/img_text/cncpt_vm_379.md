#

This graphic depicts a database instance as a large box. Inside this box is the SGA. Inside the SGA is the database buffer cache and the IM column store. Inside the IM column store are sales, customers, and products tables. Inside products are IMCU 1 and IMCU 2. Inside customers are IMCU 3 and IMCU 4. Inside sales are IMCU 5 and IMCU 6. Below the instance is a cylinder representing disk. Inside the disk are the sh tables. An arrow points from these tables both to the IM column store and the database buffer cache.
