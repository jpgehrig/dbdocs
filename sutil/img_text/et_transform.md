#

    et_transform ::=

     column_name FROM
     {
      NULL |

      CONSTANT string |

      CONCAT (field_name | CONSTANT string ,) ... |

      LOBFILE (fieldname | CONSTANT string: ,) ...

       [lobfile_attr_list] |

      STARTOF source_field (length)
     }
