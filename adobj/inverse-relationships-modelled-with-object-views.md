You can use views with objects to model inverse relationships.

### One-to-One Relationships

One-to-one relationships can be modeled with inverse object references. For example, suppose that each employee has a particular desktop computer, and that the computer belongs to that employee only.

A relational model would capture this using foreign keys either from the computer table to the employee table, or in the reverse direction. Using views, you can model the objects so there is an object reference from the employee to the computer object and also a reference from the computer object to the employee.

### One-to-Many and Many-to-One Relationships

One-to-many relationships (or many-to-many relationships) can be modeled either by using object references or by embedding the objects.

One-to-many relationship can be modeled by having a collection of objects or object references. The many-to-one side of the relationship can be modeled using object references.

Consider the department-employee case. In the underlying relational model, the foreign key is in the employee table. The relationship between departments and employees can be modeled using collections in views. The department view can have a collection of employees, and the employee view can have a reference to the department (or inline the department values). This gives both the forward relation (from employee to department) and the inverse relation (department to list of employees). The department view can also have a collection of references to employee objects instead of embedding the employee objects.
