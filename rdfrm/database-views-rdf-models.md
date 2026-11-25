## 14.3.2.12 Database Views from RDF Models

You can create relational views from RDF models. These views can represent a vertex or an edge view of a graph.

SPARQL query patterns can be used as a declarative language for specifying how to build vertex and edge views from RDF data.

It is important to note the following when creating the vertex and edge views from an RDF model:

- The RDF model must have classes defined and the application uses a SPARQL query to retrieve the distinct classes defined on an RDF model. For example:

      SELECT DISTINCT ?o
      WHERE { ?s a ?o } order by ?o

- One or more RDF classes can define a vertex view. A vertex view consists of:
  - Database vertex view name
  - Key attribute name
  - Vertex properties from RDF class

- One or two vertex views can define an edge view. An edge view consists of:
  - Database edge view name
  - Source and destination vertex keys
  - Label property from RDF classes

The following sections explain the steps to create a database graph view:

- [Creating a Graph View](creating-graph-view.md)
- [Creating a Vertex View](creating-vertex-view.md)
- [Creating an Edge View](creating-edge-view.md)

**Parent topic:** [RDF Data Page](rdf-data-page.md)
