dropwizard-dbdeploy
===================

Embedded dbdeploy for dropwizard


This project provides a class that extends dropwizard database configuration class. 
This can be exploited by providing a yaml file such as:

```yaml

database:
    # Supports all of the standard dropwizard database parameters
    driverClass: com.mysql.jdbc.Driver
    user       : root
    password   : 
    url        : jdbc:mysql://localhost:3306/demando
    
    # Provides a map of "script name" => "script classpath location" that can be used by the run command
    scripts: 
       drop    : scripts/other/drop.sql
       create  : scripts/changelog/createSchemaVersionTable.mysql.sql
     
    # Configures the dbdeploy instance
    dbdeploy:

       # The location of the classpath folder that contains all of the deltas 
       scriptLocation : scripts/deltas/

       # The name of the dbms. Possible options include: db2, hsql, mssql, mysql, ora, syb-ase 
       dbms           : mysql

       # The delimiter between statements, defaults to ';' 
       delimiter      : ;

       # The type of delimiter 'normal' (delimiter can appear anywhere) or 'row' (must be on a row on its own), defaults to 'normal' 
       delimiterType  : normal
       
       # The encoding present in the script/delta files, defaults to 'UTF-8' 
       encoding       : UTF-8
   
       # The number of the last delta to apply. This is optional with no default
       lastChangeToApply : 001

       # The line style of line ending present in the script/delta files. Possible options include : platform, cr, crlf, lf. Defaults to platform line seperator.
       lineEnding : platform
 
       # Specifying this file means that instead of applying the delta to the database, it generates one script with all of the applicable deltas.
       outputFile : output.sql
   
       # Overide the default undo and apply script templates. This is optional 
       templatesLocation : db/templates

       # Specifying this file will generate an undo file in this specific location. This is optional
       undoOutputFile : undoOutput.sql
    
```
