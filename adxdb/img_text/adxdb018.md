The figure illustrates the difference between `RESOURCE_VIEW` and `PATH_VIEW`. In a typical tree, `RESOURCE_VIEW` has only one path. Because many Internet applications need only one URL to access a resource, `RESOURCE_VIEW` is widely applicable. With `PATH_VIEW`, you create a link to access the target resource node, which provides two access paths to the target node for faster access.

`RESOURCE_VIEW` Example:

    select path(1) from RESOURCE_VIEW where under_path(res,'/sys',1);

displays one path to the resource:

    /home/corp/po_westcoast

`PATH_VIEW` Example:

    select path from PATH_VIEW;

displays all paths to the resource:

    /home/corp/po_westcoast
    /home/role/po_eastcoast
