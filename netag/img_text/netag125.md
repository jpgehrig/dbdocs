# Description of the illustration netag125.eps

This illustration shows the two instances described in the surrounding text. The instance called sales1 is configured with the following parameter settings in its initialization parameter file:

    SERVICE=NAME=sales.us.example.com
    INSTANCE_NAME=sales1
    REMOTE_LISTENER=listener_sales2

The instance called sales2 is configured with the following parameter settings in its initialization parameter file:

    SERVICE=NAME=sales.us.example.com
    INSTANCE_NAME=sales2
    REMOTE_LISTENER=listener_sales1
