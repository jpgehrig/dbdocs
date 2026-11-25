Consider the columns of `PRINT_MEDIA` table of `PM` sample schema.

- Table PM.PRINT_MEDIA

### 4.7.1 Table PM.PRINT_MEDIA

Table 4-21 PM.PRINT_MEDIA Table Description

| Column Name        | Null?      | Type              |
|:-------------------|:-----------|:------------------|
| `PRODUCT_ID`       | `NOT NULL` | `NUMBER(6)`       |
| `AD_ID`            | `NOT NULL` | `NUMBER(6)`       |
| `AD_COMPOSITE`     |            | `BLOB`            |
| `AD_SOURCETEXT`    |            | `CLOB`            |
| `AD_FINALTEXT`     |            | `CLOB`            |
| `AD_FLTEXTN`       |            | `NCLOB`           |
| `AD_TEXTDOCS_NTAB` |            | `TEXTDOC_TAB`     |
| `AD_PHOTO`         |            | `BLOB`            |
| `AD_GRAPHIC`       |            | `BINARY FILE LOB` |
| `AD_HEADER`        |            | `ADHEADER_TYP`    |
