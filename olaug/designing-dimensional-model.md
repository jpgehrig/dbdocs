This guide uses the Global schema for its examples. This appendix explores the business requirements of the fictitious Global Computing Company and discusses how the design of a data model emerges from these requirements.

This appendix contains the following topics:

- Case Study Scenario

- Identifying Required Business Facts

- Designing a Dimensional Model for Global Computing

### A.1 Case Study Scenario

The fictional Global Computing Company was established in 1990. Global Computing distributes computer hardware and software components to customers on a worldwide basis. The Sales and Marketing department has not been meeting its budgeted numbers. As a result, this department has been challenged to develop a successful sales and marketing strategy.

Global Computing operates in an extremely competitive market. Competitors are numerous, customers are especially price-sensitive, and profit margins tend to be narrow. In order to grow profitably, Global Computing must increase sales of its most profitable products.

Various factors in Global Computing's current business point to a decline in sales and profits:

- Traditionally, Global Computing experiences low third-quarter sales (July through September). However, recent sales in other quarters have also been lower than expected. The company has experienced bursts of growth but, for no apparent reason, has had lower first-quarter sales during the last two years as compared with prior years.

- Global has been successful with its newest sales channel, the Internet. Although sales within this channel are growing, overall profits are declining.

- Perhaps the most significant factor is that margins on personal computers - previously the source of most of Global Computing's profits - are declining rapidly.

Global Computing must understand how each of these factors is affecting its business.

Current reporting is done by the IT department, which produces certain standard reports on a monthly basis. Any ad hoc reports are handled on an as-needed basis and are subject to the time constraints of the limited IT staff. Complaints have been widespread within the Sales and Marketing department regarding the delayed response to report requests. Complaints have also been numerous in the IT department regarding analysts who change their minds frequently or ask for further information.

The Sales and Marketing department has been struggling with a lack of timely information about what it is selling, who is buying, and how they are buying. In a meeting with the CIO, the VP of Sales and Marketing states, "By the time I get the information, it is no longer useful. I am only able to get information at the end of each month, and it does not have the details I need to do my job."

#### A.1.1 Reporting Requirements

When asked to be more specific about what she needs, the Vice President of Sales and Marketing identifies the following requirements:

- Trended sales data for specific customers, regions, and segments.

- The ability to provide information and some analysis capabilities to the field sales force. A web interface would be preferred, since the sales force is distributed throughout the world.

- Detail regarding mail-order, phone, and email sales on a monthly and quarterly basis, and a comparison to past time periods. Information must identify when, how, and what is being sold by each channel.

- Margin information on products to understand the dollar contribution for each sale.

- Knowledge of percent change versus the prior and year-ago period for sales, units, and margin.

- The ability to perform analysis of the data by ad hoc groupings.

The CIO has discussed these requirements with his team and has concluded that a standard reporting solution against the production order entry system would not be flexible enough to provide the required analysis capabilities. The reporting requirements for business analysis are so diverse that the projected cost of development, along with the expected turnaround time for requests, would make this solution unacceptable.

The CIO's team recommends using an analytic workspace to support analysis. The team suggests that the Sales and Marketing department's IT group work with Corporate IT to build an analytic workspace that meets their needs for information analysis.

#### A.1.2 Business Goals

The development team identifies the following high-level business goals that the project must meet:

- Global Computing's strategic goal is to increase company profits by increasing sales of higher margin products and by increasing sales volume overall.

- The Sales and Marketing department objectives are to:

  - Analyze industry trends and target specific market segments.

  - Analyze sales channels and increase profits.

  - Identify product trends and create a strategy for developing the appropriate channels.

#### A.1.3 Information Requirements

Once you have established business goals, you can determine the type of information that helps achieve these goals. To understand how end users examine the data in the analytic workspace, it is important to conduct extensive interviews. From interviews with key end users, you can determine how they look at the business, and what types of business analysis questions they want to answer.

##### A.1.3.1 Business Analysis Questions

Interviews with the VP of Sales and Marketing, salespeople, and market analysts at Global Computing reveal the following business analysis questions:

- What products are profitable?

- Who are our customers, and what and how are they buying?

- What accounts are most profitable? What is the performance of each distribution channel?

- Is there still a seasonal variance to the business?

We can examine each of these business analysis questions in detail.

##### What products are profitable?

This business analysis question consists of the following questions:

- What is the percent of total sales for any item, product family, or product class in any month, quarter or year, and in any distribution channel? How does this percent of sales differ from a year ago?

- What is the unit price, unit cost, and margin for each unit for any item in any particular month? What are the price, cost, and margin trends for any item in any month?

- What items were most profitable in any month, quarter, or year, in any distribution channel, and in any geographic area or market segment? How did profitability change from the prior period? What was the percent change in profitability from the prior period?

- What items experienced the greatest change in profitability from the prior period?

- What items contributed the most to total profitability in any month, quarter, or year, in any distribution channel, and in any geographic area or market segment?

- What items have the highest per unit margin for any particular month?

- In summary, what are the trends?

##### Who are our customers, and what and how are they buying?

This business analysis question consists of the following questions:

- What were sales for any item, product family, or product class in any month, quarter, or year?

- What were sales for any item, product family, or product class in any distribution channel, geographic area, or market segment?

- How did sales change from the prior period? What was the percent change in sales from the prior period?

- How did sales change from a year ago? What was the percent change in sales from a year ago?

- In summary, what are the trends?

##### Which accounts are most profitable?

This business analysis question consists of the following questions:

- Which accounts are most profitable in any month, quarter, or year, in any distribution channel, by any item, product family, or product class?

- What were sales and extended margin (gross profit) by account for any month, quarter, or year, for any distribution channel, and for any product?

- How does account profitability compare to the prior time period?

- Which accounts experienced the greatest increase in sales as compared to the prior period?

<!-- -->

- What is the percent change in sales from the prior period? Did the percent change in profitability increase at the same rate as the percent change in sales?

- In summary, what are the trends?

##### What is the performance of each distribution channel?

This business analysis question consists of the following questions:

- What is the percent of sales to total sales for each distribution channel for any item, product family, or product class, or for any geographic area or market segment?

- What is the profitability of each distribution channel: direct sales, catalog sales, and the Internet?

- Is the newest distribution channel, the Internet, "cannibalizing" catalog sales? Are customers simply switching ordering methods, or is the Internet distribution channel reaching additional customers?

- In summary, what are the trends?

##### Is there still a seasonal variance to the business?

This business analysis question consists of the following questions:

- Are there identifiable seasonal sales patterns for particular items or product families?

- How do seasonal sales patterns vary by geographic location?

- How do seasonal sales patterns vary by market segment?

- Are there differences in seasonal sales patterns as compared to last year?

##### A.1.3.2 Summary of Information Requirements

By examining the types of analyses that users want to perform, we can identify the following key requirements for analysis:

- Global Computing has a strong need for profitability analysis. The company must understand profitability by product, account, market segment, and distribution channel. It also must understand profitability trends.

- Global Computing must understand how sales vary by time of year. The company must understand these seasonal trends by product, geographic area, market segment, and distribution channel.

- Global Computing has a need for ad hoc sales analysis. Analysis must identify what products are sold to whom, when these products are sold, and how customers buy these products.

- The ability to perform trend analysis is important to Global Computing.

### A.2 Identifying Required Business Facts

The key analysis requirements reveal the business facts that are required to support analysis requirements at Global Computing.

These facts are ordered by time, product, customer shipment or market segment, and distribution channel:

- Sales
- Units
- Change in sales from prior period
- Percent change in sales from prior period
- Change in sales from prior year
- Percent change in sales from prior year
- Product share
- Channel share
- Market share
- Extended cost
- Extended margin
- Extended margin change from prior period
- Extended margin percent change from prior period
- Units sold, change from prior period
- Units sold, percent change from prior period
- Units sold, change from prior year
- Units sold, percent change from prior year
-

These facts are ordered by item and month:

- Unit price
- Unit cost
- Margin per unit

### A.3 Designing a Dimensional Model for Global Computing

"Business Goals" identifies the business facts that support analysis requirements at Global Computing. Next, we identify the dimensions, levels, and attributes in a data model. We also identify the relationships within each dimension. The resulting data model is used to design the Global schema, the dimensional model, and the analytic workspace.

#### A.3.1 Identifying Dimensions

Four dimensions are used to organize the facts in the database:

- Product shows how data varies by product.

- Customer shows how data varies by customer or geographic area.

- Channel shows how data varies according to each distribution channel.

- Time shows how data varies over time.

#### A.3.2 Identifying Levels

Now that we have identified dimensions, we can identify the levels of summarization within each dimension. Analysis requirements at Global Computing reveal that:

- There are three distribution channels: Sales, Catalog, and Internet. These three values are the lowest level of detail in the data warehouse and are grouped in the Channel level. From the order of highest level of summarization to the lowest level of detail, the levels are Total and Channel.

- Global performs customer and geographic analysis along the line of shipments to customers and by market segmentation. Shipments and Market are two hierarchies in the Customer dimension. In each case, the lowest level of detail in the data model is the Ship To location.

  - When analyzing along the line of customer shipments, the levels of summarization are (highest to lowest): Total, Region, Warehouse, and Ship To.

  - When analyzing by market segmentation, the levels of summarization are (highest to lowest): Total, Market Segment, Account, and Ship To.

<!-- -->

- The Product dimension has four levels (highest to lowest): Total, Class, Family, and Item.

- The Time dimension has four levels (highest to lowest): Total, Year, Quarter, and Month. The dimension has two hierarchies: Calendar and Fiscal.

All dimensions have a Total level as the highest level of summarization. Adding this highest level provides additional flexibility as application users analyze data.

#### A.3.3 Identifying Hierarchies

We can identify the hierarchies that organize the levels within each dimension. To identify hierarchies, we group the levels in the correct order of summarization and in a way that supports the identified types of analysis.

For the Channel and Product dimensions, Global Computing requires only one hierarchy for each dimension. For the Customer dimension, Global Computing requires two hierarchies. Analysis within the Customer dimension tends to be either by geographic area or market segment. Therefore, we organize levels into two hierarchies, Shipments and Segment. Analysis over time also requires two hierarchies, a Calendar hierarchy and a Fiscal hierarchy.

#### A.3.4 Identifying Stored Measures

"Identifying Required Business Facts" lists 21 business facts that are required to support the analysis requirements of Global Computing. Of this number, only four facts must be acquired from the transactional database:

- Units

- Sales

- Unit Price

- Unit Cost

All of the other facts can be derived from these basic facts. The derived facts can be calculated in the analytic workspace on demand. If experience shows that some of these derived facts are being used heavily and the calculations are putting a noticeable load on the system, then some of these facts can be calculated and stored in the analytic workspace as a data maintenance procedure.
