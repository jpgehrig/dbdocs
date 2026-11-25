# Description of the illustration netag034.eps

This illustration depicts two instances. The general description of the instance is described in the surrounding text. sales1 is configured with the following parameter settings in its initialization parameter file:

    SERVICE=NAME=sales.us.example.com
    INSTANCE_NAME=sales1
    DISPATCHERS=(PROTOCOL=tcp)(DISPATCHERS=1)(LISTENER=listeners_sales)

sales2 is configured with the following parameter settings in its initialization parameter file:

    SERVICE=NAME=sales.us.example.com
    INSTANCE_NAME=sales2
    DISPATCHERS=(PROTOCOL=tcp)(DISPATCHERS=2)(LISTENER=listeners_sales)
