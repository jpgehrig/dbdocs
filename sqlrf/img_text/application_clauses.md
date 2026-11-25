# Description of the illustration application_clauses

    APPLICATION
    { { app_name
        { BEGIN INSTALL 'app_version' [ COMMENT 'comment' ]
        | END INSTALL [ 'app_version' ]
        | BEGIN PATCH number [ MINIMUM VERSION 'app_version' ] [ COMMENT 'comment' ]
        | END PATCH [ number ]
        | BEGIN UPGRADE [ 'start_app_version' ] TO 'end_app_version' [ COMMENT 'comment' ]
        | END UPGRADE [ TO 'end_app_version' ]
        | BEGIN UNINSTALL
        | END UNINSTALL
        | SET PATCH number
        | SET VERSION 'app_version'
        | SET COMPATIBILITY VERSION { 'app_version' | CURRENT }
        | SYNC TO { ' app_version ' | PATCH patch_number }
        | SYNC  }
      |
      { ALL SYNC }
    }
