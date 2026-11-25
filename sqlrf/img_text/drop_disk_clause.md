# Description of the illustration drop_disk_clause.eps

    DROP
    { [ QUORUM | REGULAR ] DISK
        disk_name [ FORCE | NOFORCE ]
        [, disk_name [ FORCE | NOFORCE ] ]...
    | DISKS IN [ QUORUM | REGULAR ] FAILGROUP
        failgroup_name [ FORCE | NOFORCE ]
        [, failgroup_name [ FORCE | NOFORCE ] ]...
    }
