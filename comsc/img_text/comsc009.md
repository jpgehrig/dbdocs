This figure shows the structure of schema PM and its relationships with table `oe.product_information`.

The `print_media` table has the following attributes:

- Columns: `product_id`(primary key), `ad_id`, `ad_composite`, `ad_sourcetext`, `ad_finaltext`, `ad_fltextn`, `ad_textdocs_ntab`, `ad_photo`, `ad_graphic`, and `ad_header`

- Other Relationships:

  - Column `product_id` relates one or more rows of the table `print_media` to one row of the table `oe.product_information` with the corresponding value of `product_id`.
