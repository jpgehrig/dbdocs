The figure shows two XML documents at the upper left, as follows:

XML instance document: employees.xml

    ...
    <employee>
      <first_name>Shelli</first_name>
      <last_name>Baida</last_name>
      <email>sbaida</email>
       ...
      <hire_date>24-DEC-97</hire_date>
       ...
      <department_id>30</department_id>
    </employee>
    ...

XML schema: employee.xsd

    ...
    <sequence>
      <element name="first_name" type="string"/>
      <element name="last_name" type="string"/>
      <element name="email" type="string"/>
       ...
      <element name="hire_date" type="date"/>
       ...
      <element name="dept_id" type="integer"/>
    </sequence>
    ...

There is an arrow from each of the XML documents to a box labeled "Create XMLTYpe Table". From this box there are two arrows, each pointing to a box representing database tables. These arrows are labeled, from left to right, "Binary XML Storage", and "Object-Relational Storage". The table boxes are labeled, from left to right, "XML data stored as binary XML" and "XML data stored in object-relational columns and tables".

Inside each database-tables box is the label "employees Tables" and a depiction of database columns. The binary XML storage box shows a column labeled "XMLType column". The entries in this column are shown as "Binary XML". The object-relational storage box shows columns labeled "first_name", "last_name", "email", and "dept_id". A row is shown with corresponding entries "shelli", "baida", "sbaida", and "30".
