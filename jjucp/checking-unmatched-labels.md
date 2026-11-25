A connection may have multiple labels that each uniquely identifies the connection based on some desired criteria. The `getUnmatchedConnectionLabels` method is used to verify which connection labels matched from the requested labels and which did not. The method is used after a connection with multiple labels is borrowed from the connection pool and is typically used by a labeling callback. The following example demonstrates checking for unmatched labels.

    String pname = "property1";
    String pvalue = "value";
    Properties label = new Properties();
    label.setProperty(pname, pvalue);

    Connecion conn = pds.getConnection(label);
    Properties unmatched = ((LabelableConnection)
       connection).getUnmatchedConnectionLabels (label);
