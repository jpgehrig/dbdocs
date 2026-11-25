# Description of the illustration password_parameters.eps

    { { FAILED_LOGIN_ATTEMPTS
      | PASSWORD_LIFE_TIME
      | PASSWORD_REUSE_TIME
      | PASSWORD_REUSE_MAX
      | PASSWORD_LOCK_TIME
      | PASSWORD_GRACE_TIME
      | INACTIVE_ACCOUNT_TIME
      }
      { expr | UNLIMITED | DEFAULT }
    | PASSWORD_VERIFY_FUNCTION
      { function | NULL | DEFAULT }
    | ( PASSWORD_ROLLOVER_TIME { expr | DEFAULT } )
    }
