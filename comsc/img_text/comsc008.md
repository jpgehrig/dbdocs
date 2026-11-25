This figure shows the relational tables in schema HR and the columns in each table, as well as dependencies between the tables.

The `employees` table has the following attributes:

- Columns: `employee_id` (primary key), `first_name`, `last_name`, `email`, `phone_number`, `hire_date`, `job_id`, `salary`, `commission_pct`, `manager_id`, `department_id`.

- Relationships:

  - Column `department_id` relates each row of the table `employees` to exactly one value of `department_id` in the table `departments`

  - Column `job_id` relates each row of the table `employees` to exactly one value of `job_id` in the table `jobs`

  - Column `employee_id` relates each row of the table `employees` to none or more rows of `employee_id` in the `job_history` table

  - Column `manager_id` references none or one other row of the `employees` table through a matching `employee_id`; note that a head of the company would typically not have a manager

- Other relationships:

  - Column `employee_id` relates rows of the table `employees` to `sales_rep_id` columns in the table `oe.orders`

  - Column `employee_id` relates rows of the table `employees` to `account_mgr_id` columns in the table `oe.customers`

The `jobs` table has the following attributes:

- Columns: `job_id` (primary key), `job_title`, `min_salary`, and `max_salary`

- Relationships:

  - Column `job_id` relates each row of the table `jobs` to the corresponding values in the `jobs_id` column of the table `employees`

  - Column `job_id` relates none or more rows of the table `jobs` to the corresponding values in the `jobs_id` column of the table `job_history`

The `job_history` table has the following attributes:

- Columns: `employee_id` and `start_date` (a composite primary key), `end_date`, `job_id`, and `department_id`.

- Relationships:

  - Each `job_history` record is associated with a record in the table `employees` through the `employee_id`.

The `departments` table has the following attributes:

- Columns: `department_id` (primary key), `department_name`, `manager_id`, and `location_id`.

- Relationships:

  - Column `department_id` relates each row of the table `departments` to none or more rows of the table `employees` that have corresponding values for `department_id`.

  - Column `manager_id` relates each row of the table `departments` to a row of the table `employees` that has the corresponding value for `employee_id`.

  - Column `location_id` relates each row of the table `departments` to a row of the table `locations` that has the corresponding value for `location_id`.

The `locations` table has the following attributes:

- Columns: `location_id` (primary key), `street_address`, `postal_code`, `city`, `state_province`, and `country_id`.

- Relationships:

  - Column `location_id` relates each row of the table `locations` to none or more rows of the table `departments` that have the corresponding values for `location_id`.

  - Column `country_id` relates each row of the table `locations` to a row in the table `countries` that has the corresponding value for `country_id`.

- Other relationships:

  - Column `location_id` relates rows of the table `locations` to none or more rows of the table `eo.warehouses` that have the corresponding values for `loacation_id`.

The `countries` table has the following attributes:

- Columns: `country_id` (primary key), `country_name`, and `region_id`.

- Relationships:

  - Column `region_id` relates each row of the table `countries` to a row in the table `regions` that has the corresponding value for `region_id`.

  - Column `country_id` relates each row of the table `countries` to none or more rows in the table `locations` that have the corresponding values for `country_id`.

The `regions` table has the following attributes:

- Columns: `region_id` (primary key), and `region_name`.

- Relationships:

  - Column `region_id` relates rows of the table `regions` to none or more rows of the table `countries` that have the corresponding values for `region_id`.

This graphic also describes schema `OE` and shows the dependencies between the two schemas.

The `order_items` table has the following attributes:

- Columns: `order_id` (primary key), `line_item_id`, `product_id`, `unit_price`, and `quantity`.

- Relationships:

  - Column `order_id` relates one or more rows of the table `order_items` to one row of the table `orders` with the corresponding value of `order_id`.

  - Column `product_id` relates one or more rows of the table `order_items` to one row of the table `product_information` with the corresponding value of `product_id`.

The `orders` table has the following attributes:

- Columns: `order_id`(primary key), `order_date`, `order_mode`, `customer_id`, `order_status`, `order_total`, `sales_rep_id`, `promotion_id`

- Relationships:

  - Column `order_id` relates one row of the table `orders` to one or more rows of the table `order_items` with the corresponding values of the `order_id`.

  - Column `customer_id` relates one or more rows of the table `orders` to one row of the table `customers` with the corresponding value of customer_id.

- Other Relationships:

  - Column `sales_rep_id` relates one or more rows of the table `orders` to one row of the table `hr.employees` with the corresponding value of `employee_id`.

The `product_information` table has the following attributes:

- Columns: `product_id`(primary key), `product_name`, `product_description`, `category_id`, `weight_class`, `warranty_period`, `supplier_id`, `product_status`, `list_price`, `product_id`, `min_price`, and `catalog_url`

- Relationships:

  - Column `product_id` relates one row of the table `product_information` to one or more rows of the table `order_items` with the corresponding value of `product_id`.

  - Column `product_id` relates one row of the table `product_information` to zero or more rows of the table `product_descriptions` with the corresponding value of `product_id`.

  - Column `product_id` relates one row of the table `product_information` to zero or more rows of the table `inventories` with the corresponding value of `product_id`.

The `product_descriptions` table has the following attributes:

- Columns: `product_id` and `language_id` (composite primary key), `translated_name`, and `translated_description`

- Relationships:

  - Column `product_id` relates one or more rows of the table `product_descriptions` to a row of the table `product_information` with the corresponding value of `product_id`.

The `inventories` table has the following attributes:

- Columns: `product_id` and `warehouse_id` (composite primary key), and `quantity_on_hand`.

- Relationships:

  - Column `product_id` relates one or more rows of the table `inventories` to one row of the table `product_information` with the corresponding value of `product_id`.

  - Column `warehouse_id` relates one or more rows of the table `inventories` to one rows of the table `warehouses` with the corresponding value of `warehouse_id`.

The `customers` table has the following attributes:

- Columns: `customer_id` (primary key), `cust_first_name`, `cust_last_name`, `cust_address`, `phone_numbers`, `nls_language`, `nls_territory`, `credit_limit`, `cust_email`, `account_mgr_id`, `cust_geo_location`, `date_of_birth`, `marital_status`, `gender`, and `income_level`

- Relationships:

  - Column `customer_id` relates rows of the table `customers` to one or more rows of the table `orders` with the corresponding value of `customer_id`.

- Other Relationships:

  - Column `acct_mgr_id` relates one or more rows of the table `customers` to one row of the table `hr.employees` with the corresponding value of `employee_id`.

The `warehouses` table has the following attributes:

- Columns: `warehouse_id` (primary key), `warehouse_spec`, `warehouse_name`, `location_id`, and `wh_geo_location`

- Relationships:

  - Column `warehouse_id` relates rows of the table `warehouses` to one or more rows of the table `inventories` with the corresponding value of `warehouse_id`.

- Other Relationships:

  - Column `location_id` relates one or more rows of the table `warehouses` to one row of the table `hr.locations` with the corresponding value of `location_id`.
