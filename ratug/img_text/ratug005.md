# Description of the illustration ratug005.png

This diagram shows a scenario for setting up a test system to consolidate three workload captures from three separate production systems. There are two main parts in this diagram.

The upper part of the diagram consists of a dotted box labeled Production Systems. It contains three databases, labeled CRM - DB 10.2.0.4, ERP - DB 10.2.0.5, and SCM - 11.2.0.2:

- The CRM database is connected a workload capture named cap_crm.

- The ERP database is connected a workload capture named cap_erp.

- The SCM database is connected a workload capture named cap_scm.

An arrow points down from the Production Systems part to the lower part of the diagram.

The lower part of the diagram consists of a dotted box labeled Test System. It contains a dotted box labeled Consolidated Capture, and a large database labeled CDB - DB 12.1.0.1. The Consolidated Capture dotted box contains a directory named u01/test/cons_dir. Under this directory are three workload captured labeled cap_crm, cap_erp, and cap_scm. The Consolidated Capture dotted box is connected to the CDB - DB 12.1.0.1 database. The CDB - DB 12.1.0.1 database contains three smaller PDB databases labeled CRM, ERP, and SCM.

End of description.
