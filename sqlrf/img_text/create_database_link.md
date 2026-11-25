# Description of the illustration create_database_link.eps

    CREATE [ SHARED ] [ PUBLIC ] DATABASE LINK [ IF NOT EXISTS ] dblink
      [ CONNECT
         { TO { CURRENT_USER  | user IDENTIFIED BY password [ dblink_authentication ] }
         | WITH credential }
      | dblink_authentication
      ]...
      [ USING connect_string ]
