# Description of the illustration alter_database_link.eps

    ALTER [ SHARED ] [ PUBLIC ] DATABASE LINK [ IF EXISTS ] dblink_name
      { CONNECT { ( TO user IDENTIFIED BY password [ dblink_authentication ] )
                  | ( WITH credential ) }
                  }
      | dblink_authentication
      }
