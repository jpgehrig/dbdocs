# Description of the illustration alter_diskgroup.eps

    ALTER DISKGROUP
      { diskgroup_name
          { { { add_disk_clause | drop_disk_clause }
              [, { add_disk_clause | drop_disk_clause } ]...
            | resize_disk_clause
            } [ rebalance_diskgroup_clause ]
          | replace_disk_clause
          | rename_disk_clause
          | disk_online_clause
          | disk_offline_clause
          | rebalance_diskgroup_clause
          | check_diskgroup_clause
          | diskgroup_template_clauses
          | diskgroup_directory_clauses
          | diskgroup_alias_clauses
          | diskgroup_volume_clauses
          | diskgroup_attributes
          | modify_diskgroup_file
          | drop_diskgroup_file_clause
          | convert_redundancy_clause
          | usergroup_clauses
          | user_clauses
          | file_permissions_clause
          | file_owner_clause
          | scrub_clause
          | quotagroup_clauses
          | filegroup_clauses
          }
        | { diskgroup_name [, diskgroup_name ]...
          | ALL
          } { undrop_disk_clause
            | diskgroup_availability
            | enable_disable_volume
            }
      } ;
