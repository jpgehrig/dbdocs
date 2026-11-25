For many years, Oracle used the simple database schema `SCOTT`, with its two prominent tables `EMP` and `DEPT`, for various examples in documentation and training. These tables are inadequate to show the basic features of Oracle Database and other Oracle products. The sample database schemas can be used for product documentation, courseware, software development, and application demos.

### 1.1 About the Sample Schemas

The sample database schemas provide a common platform for examples in each release of the Oracle Database. The sample schemas are a set of interlinked database schemas. This set provides approach to complexity:

- Schema Human Resources (`HR`) is useful for introducing basic topics. An extension to this schema supports Oracle Internet Directory demos.

- Schema Order Entry (`OE`) is useful for dealing with matters of intermediate complexity. Many data types are available in this schema, including nonscalar data types.

- Schema Online Catalog (`OC`) is a collection of object-relational database objects built inside schema `OE`.

- Schema Product Media (`PM`) is dedicated to print media data types.

- A set of schemas gathered under the main schema name Information Exchange (`IX`) can be used to demonstrate Oracle Advanced Queuing capabilities.

- Schema Sales History (`SH`) is designed to allow for demos with large amounts of data. An extension to this schema provides support for advanced analytic processing.

- Schema Customer Orders (`CO`) is a modern schema useful for demos of e-commerce transactions. It allows the storage of semi-structured data using JSON.

### 1.2 Design Principles for Sample Schemas

The sample database schemas have been created with the following design principles in mind:

- Simplicity and ease of use. Schemas `HR` and `OE` are intentionally simple. They provide a graduated path from simple to intermediate levels of database use.

- Relevance for typical users. The base schemas and their extensions bring to the foreground the functionality that customers typically use. Only the most commonly used database objects are built automatically in the schemas. The entire set of schemas provides a foundation upon which one can expand to illustrate additional functionality.

- Extensibility. The sample schemas provide a logical and physical foundation for adding objects to demonstrate functionality beyond the fundamental scope.

- Relevance. The sample schemas are designed to be applicable to e-business and other significant industry trends (for example, XML). When this goal conflicts with the goal of simplicity, schema extensions are used to showcase the trends in focus.

### 1.3 Customer Benefits of Sample Schemas

Benefits provided by the sample schemas include the following:

- Continuity of context. When encountering the same set of tables everywhere, users, students, and developers can spend less time becoming familiar with the schema and more time understanding or explaining the technical concepts.

- Usability. Customers can use these schemas in the seed database to run examples that are shown in Oracle Database documentation and training materials. This first-hand access to examples facilitates both conceptual understanding and application development.

- Quality. Through central maintenance and testing of both the creation scripts that build the sample schemas and the examples that run against the schemas, the quality of Oracle Database documentation and training materials is enhanced.

### 1.4 Overview of the Sample Schemas

The Oracle Database sample schemas are based on a fictitious sample company that sells goods through various channels. The company operates worldwide to fill orders for products. It has several divisions, each of which is represented by a sample database schema.

Topics:

- Schema HR – Division Human Resources tracks information about the company employees and facilities.

- Schema OE – Division Order Entry tracks product inventories and sales of company products through various channels.

- Schema PM – Division Product Media maintains descriptions and detailed information about each product sold by the company.

- Schema IX – Division Information Exchange manages shipping through B2B applications.

- Schema SH – Division Sales tracks business statistics to facilitate business decisions.

- Schema CO - Division Customer Orders models a simple retail application consisting of customer, product, store and order data.

#### 1.4.1 HR Sample Schema

In the Human Resource (`HR`) records, each employee has an identification number, e-mail address, job identification code, salary, and manager. Some employees earn commissions in addition to their salary.

The company also tracks information about jobs within the organization. Each job has an identification code, job title, and a minimum and maximum salary range for the job. Some employees have been with the company for a long time and have held different positions within the company. When an employee resigns, the duration the employee was working, the job identification number, and the department are recorded.

The sample company is regionally diverse, so it tracks the locations of its warehouses and departments. Each employee is assigned to a department, and each department is identified either by a unique department number or a short name. Each department is associated with one location, and each location has a full address that includes the street name, postal code, city, state or province, and the country code.

In places where the departments and warehouses are located, the company records details such as the country name, currency symbol, currency name, and the region where the country is located geographically.

#### 1.4.2 OE Sample Schema

The company sells several products, such as computer hardware and software, music, clothing, and tools. The company maintains information about these products, such as product identification numbers, the category into which the product falls, order entry (`OE`), the weight group (for shipping purposes), the warranty period if applicable, the supplier, the availability status of the product, a list price, a minimum price at which a product will be sold, and a URL address for manufacturer information. Inventory information is also recorded for all products, including the warehouse where the product is available and the quantity on hand. Because products are sold worldwide, the company maintains the names of the products and their descriptions in several languages.

The company maintains warehouses in several locations to fulfill customer needs. Each warehouse has a warehouse identification number, name, facility description, and location identification number.

Customer information is also tracked. Each customer has an identification number. Customer records include customer name, street name, city or province, country, phone numbers (up to five phone numbers for each customer), and postal code. Some customers place orders through the Internet, so e-mail addresses are also recorded. Because of language differences among customers, the company records the native language and territory of each customer.

The company places a credit limit on its customers, to limit the amount of products they can purchase at one time. Some customers have an account manager, and this information is also recorded.

When a customer places an order, the company tracks the date of the order, how the order was placed, the current status of the order, shipping mode, total amount of the order, and the sales representative who helped place the order. The sales representative may or may not be the same person as the account manager for a customer. If an order is placed over the Internet, no sales representative is recorded. In addition to order information, the company also tracks the number of items ordered, the unit price, and the products ordered.

Schema `OE` also contains XML purchase-order documents. These are stored in Oracle XML DB Repository after validation against the registered XML schema `purchaseorder.xsd`. You can access these documents in various ways, such as by querying table `purchaseorder` using SQL, querying public views `RESOURCE_VIEW` and `PATH_VIEW`, and querying the repository using XPath expressions.

The purchase-order XML documents are located in Oracle XML DB Repository folder `$ORACLE_HOME``/rdbms/demo/order_entry/2002/``month`, where `month` is a three-letter month abbreviation (for example, `Jan`, `Feb`, `Mar`).

#### 1.4.3 OC Sample Schema

The Online Catalog (`OC`) subschema of database schema `OE` addresses an online catalog merchandising scenario. The same customers and products are used in `OC` as in schema `OE` proper, but subschema `OC` organizes the products into a hierarchy of parent categories and subcategories. This hierarchy corresponds to the arrangement on an e-commerce portal site, where users navigate to specific products by drilling down through increasingly specialized categories of products.

#### 1.4.4 PM Sample Schema

The company stores print information about its products in a database. The Product Media (`PM`) schema is used to store such information. Examples of such information are:

- Press release texts

- Print media advertisements

- Other promotional texts and translations

#### 1.4.5 IX Sample Schema

The company has decided to test the use of messaging to manage its proposed B2B applications. The plan calls for a small test that will allow a user from outside the firewall to place an order and track its status. The order must be booked into the main system. Then, depending on the location of the customer, the order is routed to the nearest region for shipping. The Information Exchange (IX) schema stores such information.

Eventually, the company intends to expand beyond its current in-house distribution system to a system that will allow other businesses to provide the shipping. The messages sent must be in a self-contained format. XML is the perfect format for sending messages, and both Advanced Queuing Servlet and Oracle Internet Directory provide the required routing between the queues.

After the orders are either shipped or back ordered, a message must be sent back to the employee concerned to inform about the status of the order and to initiate the billing. It is important that the message be delivered only once and that there be a system for tracking and reviewing messages to facilitate resolution of any discrepancies with the order.

For the purpose of this test application, the company uses a database server and an application server. The application provides a mechanism for examining the XML messages as well as monitoring the queues. To demonstrate connectivity from outside the firewall, both the generation of a new order and customer service reporting are performed using queues. The new order application directly enables a queue, while the customer service queries require XML messaging to disable a queue.

#### 1.4.6 SH Sample Schema

The sample company does a high volume of business, so it runs business statistics reports to aid in decision making. Many of these reports are time-based and nonvolatile. That is, they analyze past data trends. The company loads data into its data warehouse regularly to gather statistics for these reports. These reports include annual, quarterly, monthly, and weekly sales figures by product. These reports are stored with the help of schema Sales History (`SH`).

The company also runs reports on distribution channels through which its sales are delivered. When the company runs special promotions on its products, it analyzes the impact of the promotions on sales. It also analyzes sales by geographical area.

#### 1.4.7 CO Sample Schema

The Customer Orders (CO) schema records the details of transactions made by a retail application.

The CO schema is similar in concept to the OE schema. The CO schema is modern and highlights the features of Oracle database 12c such as JSON support.

The company sells a variety of products which is maintained in the `products` table. Each product has a unique identification number, name, price, details stored in a JSON object and product image details.

The orders placed by the customer is tracked using the order identification number, date and time when the order was placed, customer details, order status and the store information.

The details of the products in a particular order is also tracked using the order identification number. Details of the product(s), price at the time of purchase and quantity are recorded.

The information of a customer placing an order is tracked. Each customer has an identification number, name and email address which is used for communication of the orders.

The customers can purchase the products in stores or online through the company's website. The company stores the information of all the stores and their corresponding physical and virtual addresses. The information of the store is also recorded in the order details.
