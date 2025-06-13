##### Sqoop-Big-Data

- **Apache Sqoop** is a tool in the Hadoop ecosystem designed for efficiently transferring bulk data between structured data stores (like RDBMS) and Hadoop ecosystems (like HDFS, Hive, HBase).

- From RDBMS → Hadoop: Import data from MySQL, PostgreSQL, Oracle, etc. into HDFS, Hive, HBase.
- From Hadoop → RDBMS: Export data from Hadoop back to relational databases.

##### Theory and Features

- Import/export data between RDBMS and HDFS/Hive/HBase.

- Supports parallel import/export (uses MapReduce internally).

- Supports various databases via JDBC: MySQL, Oracle, Postgres, SQL Server, etc.

- Can import entire tables or specific SQL queries.

- Generates Java classes from table schema.

- Supports incremental data import (append and lastmodified modes).

##### Workflow: Importing data from MySQL to HDFS

- Sqoop connects to MySQL using JDBC.

- Metadata is fetched (table schema).

- Sqoop splits data for parallel processing using split-by column.

- Mappers import data chunks in parallel into HDFS.

##### Import vs Export

```bash 

|   Feature     |        Import         |     Export                           |
| 	:-----:	    | 	:-----:	            | 	:-----:	                           | 
| Source        | RDBMS                 | HDFS, Hive, HBase                    |
| Destination   | Hadoop Ecosystem      | RDBMS                                |
| Use           | Load data into Hadoop | Send processed data back to database |
| Command       | sqoop import          | sqoop export                         |
```

##### Important Sqoop Options

- **--connect**  : 	JDBC connection string
- **--username,--password**  : Database credentials
- **--table**  : Table name to import
- **--target-dir**  : HDFS directory to store data
- **--split-by**  : Column used for parallel split
- **--incremental**  : Type of incremental import: append or lastmodified
- **--check-column**  : Column used for checking new data
- **--last-value**  : Last imported value
- **--fields-terminated-by**  : Custom delimiter for output files
