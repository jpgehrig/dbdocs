# Description of the illustration lnoci029.eps

This illustration shows how SQL DDL statements are used to create type definitions in the database. These type definitions are also input to OTT. The output of OTT is the implementation file and the header files. The header file is included in the OCI source code file. The source code file and the implementation file are the inputs to the C compiler. The compiler outputs object files, which are linked with the OCI library to create the executable output. This executable now has the type information from the database in it.
