## 4 Simple Knowledge Organization System (SKOS) Support

You can perform inferencing based on a core subset of the Simple Knowledge Organization System (SKOS) data model, which is especially useful for representing thesauri, classification schemes, taxonomies, and other types of controlled vocabulary.

SKOS is based on standard semantic web technologies including RDF and OWL, which makes it easy to define the formal semantics for those knowledge organization systems and to share the semantics across applications.

Support is provided for most, but not all, of the features of SKOS, the detailed specification of which is available at [`http://www.w3.org/TR/skos-reference/`](http://www.w3.org/TR/skos-reference/).

Around 40 SKOS-specific terms are included in the RDF Semantic Graph support, such as `skos:broader`, `skos:relatedMatch`, and `skos:Concept`. Over 100 SKOS axiomatic triples have been added, providing the basic coverage of SKOS semantics. However, support is not included for the integrity conditions described in the SKOS specification.

To perform SKOS-based inferencing, specify the system-defined `SKOSCORE` rulebase in the `rulebases_in` parameter in the call to the [SEM_APIS.CREATE_ENTAILMENT](SEM_APIS-reference.md) procedure, as in the following example:

    EXECUTE sem_apis.create_entailment('tstidx',sem_models('tst'), sem_rulebases('skoscore'), network_owner=>'RDFUSER', network_name=>'NET1');

Example 4-1 defines, in Turtle format, a simple electronics scheme and two relevant concepts, cameras and digital cameras. Its meaning is straightforward and its representation is in RDF. It can be managed by Oracle Database in the same way as other RDF and OWL data.

Example 4-1 SKOS Definition of an Electronics Scheme

    ex1:electronicsScheme rdf:type skos:ConceptScheme;

    ex1:cameras rdf:type skos:Concept;
       skos:prefLabel "cameras"@en;
       skos:inScheme ex1:electronicsScheme.

    ex1:digitalCameras rdf:type skos:Concept;
       skos:prefLabel "digital cameras"@en;
       skos:inScheme ex1:electronicsScheme.

    ex1:digitalCameras skos:broader ex1:cameras.

- Supported and Unsupported SKOS Semantics
  This section describes features of SKOS semantics that are and are not supported by Oracle Database.
- Performing Inference on SKOS Models
  Performing inference on a SKOS model is similar to performing inference on a semantic model.

**Parent topic:** [Conceptual and Usage Information](part-concept-usage.md)

### 4.1 Supported and Unsupported SKOS Semantics

This section describes features of SKOS semantics that are and are not supported by Oracle Database.

- Supported SKOS Semantics
- Unsupported SKOS Semantics

**Parent topic:** Simple Knowledge Organization System (SKOS) Support

#### 4.1.1 Supported SKOS Semantics

All terms defined in SKOS and SKOS extension for labels are recognized. When the SKOSCORE rulebase is chosen for inference, the recognized terms include the following:

    skos:altLabel
    skos:broader
    skos:broaderTransitive
    skos:broadMatch
    skos:changeNote
    skos:closeMatch
    skos:Collection
    skos:Concept
    skos:ConceptScheme
    skos:definition
    skos:editorialNote
    skos:exactMatch
    skos:example
    skos:hasTopConcept
    skos:hiddenLabel
    skos:historyNote
    skos:inScheme
    skos:mappingRelation
    skos:member
    skos:memberList
    skos:narrower
    skos:narrowerTransitive
    skos:narrowMatch
    skos:notation
    skos:note
    skos:OrderedCollection
    skos:prefLabel
    skos:related
    skos:relatedMatch
    skos:scopeNote
    skos:semanticRelation
    skos:topConceptOf
    skosxl:altLabel
    skosxl:hiddenLabel
    skosxl:Label
    skosxl:labelRelation
    skosxl:literalForm
    skosxl:prefLabel

Most SKOS axioms and definitions are supported including the following: S1-S8, S10-S11, S15-S26, S28-S31, S33-S36, S38-S45, S47-S50, and S53-S54. (See the SKOS detailed specification for definitions.)

Most SKOS integrity conditions are supported, including S9, S13, S27, S37, and S46.

S52 is partially supported.

S55, S56, and S57 are not supported by default.

- S55, the property chain (`skosxl:prefLabel, skosxl:literalForm`), is a subproperty of `skos:prefLabel`.

- S56, the property chain (`skosxl:altLabel, skosxl:literalForm`), is a subproperty of `skos:altLabel`.

- S57, the property chain (`skosxl:hiddenLabel, skosxl:literalForm`), is a subproperty of `skos:hiddenLabel.chains`.

However, S55, S56, and S57 can be implemented using the OWL 2 subproperty chain construct. For information about property chain handling, see Property Chain Handling.

**Parent topic:** Supported and Unsupported SKOS Semantics

#### 4.1.2 Unsupported SKOS Semantics

The following features of SKOS semantics are not supported:

- S12 and S51: The `rdfs:range` of the relevant predicates is the class of RDF plain literals. There is no check that the object values of these predicates are indeed plain literals; however, applications can perform such a check.

- S14: A resource has no more than one value of `skos:prefLabel` per language tag. This integrity condition is even beyond OWL FULL semantics, and it is not enforced in the current release.

- S32: The `rdfs:range of skos:member` is the union of classes `skos:Concept` and `skos:Collection`. This integrity condition is not enforced.

- S55, S56, and S57 are not supported by default, but they can be implemented using the OWL 2 subproperty chain construct, as explained in Supported SKOS Semantics.

**Parent topic:** Supported and Unsupported SKOS Semantics

### 4.2 Performing Inference on SKOS Models

Performing inference on a SKOS model is similar to performing inference on a semantic model.

To create an SKOS model, use the same procedure ([SEM_APIS.CREATE_SEM_MODEL](SEM_APIS-reference.md)) as for creating a semantic model. You can load data into an SKOS model in the same way as for semantic models.

To infer new relationships for one or more SKOS models, use the [SEM_APIS.CREATE_ENTAILMENT](SEM_APIS-reference.md) procedure with the system-defined rulebase `SKOSCORE`. For example:

    EXECUTE sem_apis.create_entailment('tstidx',sem_models('tst'), sem_rulebases('skoscore')), network_owner=>'RDFUSER', network_name=>'NET1');

The inferred data will include many of the axioms defined in the SKOS detailed specification. Like other system-defined rulebases, SKOSCORE has no explicit rules; all the semantics supported are coded into the implementation.

- Validating SKOS Models and Entailments
- Property Chain Handling

**Parent topic:** Simple Knowledge Organization System (SKOS) Support

#### 4.2.1 Validating SKOS Models and Entailments

You can use the [SEM_APIS.VALIDATE_ENTAILMENT](SEM_APIS-reference.md) and [SEM_APIS.VALIDATE_MODEL](SEM_APIS-reference.md) procedures to validate the supported integrity conditions. The output will include any inconsistencies caused by the supported integrity conditions, such as OWL 2 `propertyDisjointWith` and `S52`.

Example 4-2 validates an SKOS entailment.

Example 4-2 Validating an SKOS Entailment

    set serveroutput on
    declare
      lva mdsys.rdf_longVarcharArray;
      idx int;
    begin
      lva := sem_apis.validate_entailment(sdo_rdf_models('tstskos'), sem_rulebases('skoscore'), network_owner=>'RDFUSER',network_name=>'NET1');
      if (lva is null) then
        dbms_output.put_line('No conflicts');
      else
      for idx in 1..lva.count loop
        dbms_output.put_line('entry ' || idx || ' ' || lva(idx));
      end loop;
      end if;
    end;
     /

**Parent topic:** Performing Inference on SKOS Models

#### 4.2.2 Property Chain Handling

The SKOS S55, S56, and S57 semantics are not supported by default. However, you can add support for them by using the OWL 2 subproperty chain construct.

Example 4-3 inserts the necessary chain definition triples for S55 into an SKOS model. After the insertion, an invocation of [SEM_APIS.CREATE_ENTAILMENT](SEM_APIS-reference.md) that specifies the `SKOSCORE` rulebase will include the semantics defined in S55.

Example 4-3 Property Chain Insertions to Implement S55

    INSERT INTO tst VALUES(sdo_rdf_triple_s('tst','<http://www.w3.org/2004/02/skos/core#prefLabel>', '<http://www.w3.org/2002/07/owl#propertyChainAxiom>', '_:jA1', 'RDFUSER', 'NET1'));
    INSERT INTO tst VALUES(sdo_rdf_triple_s('tst','_:jA1', '<http://www.w3.org/1999/02/22-rdf-syntax-ns#first>', '<http://www.w3.org/2008/05/skos-xl#prefLabel>', 'RDFUSER', 'NET1'));
    INSERT INTO tst VALUES(sdo_rdf_triple_s('tst','_:jA1', '<http://www.w3.org/1999/02/22-rdf-syntax-ns#rest>', '_:jA2', 'RDFUSER', 'NET1'));
    INSERT INTO tst VALUES(sdo_rdf_triple_s('tst','_:jA2', '<http://www.w3.org/1999/02/22-rdf-syntax-ns#first>', '<http://www.w3.org/2008/05/skos-xl#literalForm>', 'RDFUSER', 'NET1'));
    INSERT INTO tst VALUES(sdo_rdf_triple_s('tst','_:jA2', '<http://www.w3.org/1999/02/22-rdf-syntax-ns#rest>', '<http://www.w3.org/1999/02/22-rdf-syntax-ns#nil>', 'RDFUSER', 'NET1'));

**Parent topic:** Performing Inference on SKOS Models
