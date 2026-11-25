This graphic describes the tables in schema `SH`.

The `costs` table has the following attributes:

- Columns: `prod_id`, `time_id`, `promo_id`, `channel_id`, `unit_cost`, and `unit_price`

- Relationships:

  - Column `prod_id` relates one or more rows of the table `costs` to one row of the table `products` with the corresponding value of `prod_id`.

  - Column `time_id` relates one or more rows of the table `costs` to one row of the table `times` with the corresponding value of `time_id`.

The `products` table has the following attributes:

- Columns: `prod_id` (primary key), `prod_name`, `prod_desc`, `prod_subcategory`, `prod_subcategory_id`, `prod_subcategory_desc`, `prod_category`, `prod_category_id`, `prod_category_desc`, `prod_weight_class`, `prod_unit_of_measure`, `prod_pack_size`, `supplier_id`, `prod_status`, `prod_list_price`, `prod_min_price`, `prod_total`, `prod_total_id`, `prod_src_id`, `prod_eff_from`, `prod_eff_to`, and `prod_valid`

- Relationships:

  - Column `prod_id` relates rows of the table `products` to one or more rows of the table `sales` with the corresponding value of `prod_id`.

  - Column `prod_id` relates rows of the table `products` to one or more rows of the table `costs` with the corresponding value of `prod_id`.

The `promotions` table has the following attributes:

- Columns: `promo_id` (primary key), `promo_name`, `promo_subcategory`, `promo_subcategory_id`, `promo_category`, `promo_category_id`, `promo_cost`, `promo_begin_date`, `promo_end_date`, `promo_total` and `promo_total_id`

- Relationships:

  - Column `promo_id` relates rows of the table `promotions` to one or more rows of the table `sales` with the corresponding value of `promo_id`.

The `sales` table has the following attributes:

- Columns: `prod_id`, `cust_id`, `time_id`, `channel_id`, `promo_id`, `quantity_sold`, and `amount_sold`

- Relationships:

  - Column `prod_id` relates one or more rows of the table `sales` to a row of the table `products` with the corresponding value of `prod_id`.

  - Column `promo_id` relates one or more rows of the table `sales` to a row of the table `promotions` with the corresponding value of `promo_id`.

  - Column `channel_id` relates one or more rows of the table `sales` to a row of the table `channels` with the corresponding value of `channel_id`.

  - Column `cust_id` relates one or more rows of the table `sales` to a row of the table `customers` with the corresponding value of `cust_id`.

  - Column `times_id` relates one or more rows of the table `sales` to a row of the table `times` with the corresponding value of `times_id`.

The `channels` table has the following attributes:

- Columns: `channel_id` (primary key), `channel_desc`, `channel_class`, `channel_class_id`, `channel_total`, and `channel_total_id`

- Relationships:

  - Column `channel_id` relates rows of the table `channels` to one or more rows of the table `sales` with the corresponding value of `channel_id`.

The `customers` table has the following attributes:

- Columns: `cust_id` (primary key), `cust_first_name`, `cust_last_name`, `cust_gender`, `cust_year_of_birth`, `cust_marital_status`, `cust_street_address`, `cust_postal_code`, `cust_city`, `cust_city_id`, `cust_state_province`, `cust_state_provice_id`, `country_id`, `cust_main_phone_number`, `cust_income_level`, `cust_credit_limit`, `cust_email`, `cust_total`, `cust_total_id`, `cust_src_id`, `cust_eff_from`, `cust_eff_to`, and `cust_valid`

- Relationships:

  - Column `cust_id` relates rows of the table `customers` to one or more rows of the table `sales` with the corresponding value of `customer_id`.

  - Column `country_id` relates one or more rows of the table `customers` to one row of the table `countries` with the corresponding value of `country_id`

The `times` table has the following attributes:

- Columns: `time_id` (primary key), `day_name`, `day_number_in_week`, `day_number_in_month`, `calendar_week_number`, `fiscal_week_number`, `week_ending_day`, `week_ending_day_id`, `calendar_month_number`, `fiscal_month_number`, `calendar_month_desc`, `calendar_month_id`, `fiscal_month_desc`, `fiscal_month_id`, `days_in_cal_month`, `days_in_fis_month`, `end_of_cal_month`, `end_of_fis_month`, `calendar_month_name`, `fiscal_month_name`, `calendar_quarter_desc`, `calendar_quarter_id`, `fiscal_quarter_desc`, `fiscal_quarter_id`, `days_in_cal_quarter`, `days_in_fis_quarter`, `end_of_cal_quarter`, `end_of_fis_quarter`, `calendar_quarter_number`, `fiscal_quarter_number`, `calendar_year`, `calendar_year_id`, `fiscal_year`, `fiscal_year_id`, `days_in_cal_year`, `days_in_fis_year`, `end_of_cal_year`, and `end_of_fis_year`

- Relationships:

  - Column `time_id` relates rows of the table `times` to one or more rows of the table `sales` with the corresponding value of `time_id`.

The `countries` table has the following attributes:

- Columns: `country_id` (primary key), `country_iso_code`, `country_name`, `country_subregion`, `country_subregion_id`, `country_region`, `country_region_id`, `country_total`, `country_total_id`, `country_name_hist`

- Relationships:

  - Column `country_id` relates rows of the table `countries` to one or more rows of the table `customers` with the corresponding value of `country_id`.
