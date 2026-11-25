# Description of the illustration alter_role.eps

    ALTER ROLE role
      { NOT IDENTIFIED
      | IDENTIFIED
          { BY password
          | USING [ schema. ] package
          | EXTERNALLY
          | GLOBALLY AS '{domain_name_of directory_group | ( AZURE_ROLE=value ) | ( IAM_GROUP_NAME=value )}'
          }
      }
      [ CONTAINER = { CURRENT | ALL } ] ;
