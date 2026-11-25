# Description of the illustration alter_user

    ALTER USER [ IF EXISTS ]
      { user
        { IDENTIFIED
          { BY password [ REPLACE old_password ]
          | EXTERNALLY [ AS 'certificate_DN' | AS 'kerberos_principal_name' ]
          | GLOBALLY [ AS '{  directory_DN  |  {AZURE_USER | AZURE_ROLE }=value
                               | {IAM_GROUP_NAME | IAM_PRINCIPAL_NAME}=value  }']
          }
        | NO AUTHENTICATION
        | ADD FACTOR auth_method AS external_name
        | UPDATE FACTOR auth_method AS external_name
        | DROP FACTOR auth_method
        | DEFAULT COLLATION collation_name
        | DEFAULT TABLESPACE tablespace
        | [ LOCAL ] TEMPORARY TABLESPACE { tablespace | tablespace_group_name }
        | { QUOTA { size_clause
                  | UNLIMITED
                  } ON tablespace
          } ...
        | PROFILE profile
        | DEFAULT ROLE { role [, role ]...
                       | ALL [ EXCEPT role [, role ]... ]
                       | NONE
                       }
        | PASSWORD EXPIRE
        | ACCOUNT { LOCK | UNLOCK }
        | ENABLE EDITIONS [ FOR object_type [, object_type ]... ] [ FORCE ]
        | [HTTP] DIGEST { ENABLE | DISABLE }
        | CONTAINER = { CURRENT | ALL }
        | container_data_clause
        } ...
      | user [, user ]... proxy_clause
      }
