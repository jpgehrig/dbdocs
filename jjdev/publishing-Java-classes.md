When you load a Java class into the database, its methods are not published automatically, because Oracle Database does not know which methods are safe entry points for calls from SQL. To publish the methods, you must write call specifications, which map Java method names, parameter types, and return types to their SQL counterparts. This chapter describes how to publish Java classes with call specifications in the following sections:

- [What Are Call Specifications](about-call-specifications.md)

- [Defining Call Specifications](defining-call-specifications.md)

- [Writing Top-Level Call Specifications](writing-top-level-call-specifications.md)

- [Writing Packaged Call Specifications](writing-packaged-call-specifications.md)

- [Writing Object Type Call Specifications](writing-object-type-call-specifications.md)
