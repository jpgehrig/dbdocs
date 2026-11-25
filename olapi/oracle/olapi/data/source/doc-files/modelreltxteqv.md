Skip navigation links

This is the text equivalent of the diagram of the Oracle OLAP Java API `Model` class associations in the modelrel.jpg file. The diagram illustrates that the `getModel` method of a `Source` associates the `Source` with from zero to one `Model` objects.

The `Model` interface has a `createSolvedSource` method that returns a `Source` object. The `getAssignments` method of a `Model` associates the `Model` with from zero to many `Assignment` objects.

The `getModel` method of an `Assignment` associates it with one `Model`. The `getAssignedSource` method associates an `Assignment` with one `Source`. The `getQualifications` method associates an `Assignment` with from one to many `Qualification` objects.

The `getQualifiedSource` method of a `Qualification` associates it with one `Source`. A `LiteralQualification` extends the abstract `Qualification` class.

------------------------------------------------------------------------

Copyright © 2002, 2018, Oracle. All rights reserved.
