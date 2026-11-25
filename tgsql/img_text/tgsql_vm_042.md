# Description of the illustration tgsql_vm_042.eps

The top box contains the following statement:

SELECT \*

FROM sales

WHERE promo_id=33

OR prod_id=136;

An arrow points down to a box labeled "Query Transformer." This box points down to a box containing the following SQL statement:

SELECT \*

FROM sales

WHERE promo_id=136

UNION ALL

SELECT \*

FROM sales

WHERE promo_id=33

AND LNNVL(prod_id=136);
