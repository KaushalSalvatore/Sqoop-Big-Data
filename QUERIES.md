#### Basic Commands and Syntax for Sqoop

- **Sqoop-Import**

```
$ sqoop import (generic args) (import args)
$ sqoop-import (generic args) (import args)
```

- **Importing a Table into HDFS**

```
$ sqoop import --connect --table --username --password --target-dir 

--connect        Takes JDBC url and connects to database
--table             Source table name to be imported
--username    Username to connect to database
--password     Password of the connecting user
--target-dir     Imports data to the specified directory
```

- **Importing Selected Data from Table**

```
$ sqoop import --connect --table --username --password --columns --where 

--columns       Selects subset of columns
--where           Retrieves the data which satisfies the condition
```

- **Importing Data from Query**

```
$ sqoop import --connect --table --username --password --query 
--query           Executes the SQL query provided and imports the results
```

- **Incremental Exports**

```
$ sqoop import --connect --table --username --password --incremental --check-column --last-value 

Sqoop import supports two types of incremental imports: 

1. Append 
2. Lastmodified.

1. Append :- Append mode is to be used when new rows are continually being added with increasing values. Column should also be specified which is continually increasing with --check-column. Sqoop imports rows whose value is greater than the one specified with --last-value.

2. Lastmodified :- Lastmodified mode is to be used when records of the table might be updated, and each such update will set the current timestamp value to a last-modified column. Records whose check column timestamp is more recent than the timestamp specified with --last-value are imported.


```
- **Importing Data into Hive**

```
$ sqoop import --connect --table --username --password --hive-import --hive-table
 
Below mentioned Hive arguments is used with the sqoop import command to directly load data into Hive:

--hive-home	- Override $HIVE_HOME path
--hive-import -	Import tables into Hive
--hive-overwrite - Overwrites existing Hive table data
--create-hive-table	- Creates Hive table and fails if that table already exists
--hive-table - Sets the Hive table name to import
--hive-drop-import-delims - Drops delimiters like\n, \r, and \01 from string fields
--hive-delims-replacement - Replaces delimiters like \n, \r, and \01 from string fields with user defined delimiters
--hive-partition-key - Sets the Hive partition key
--hive-partition-value - Sets the Hive partition value
--map-column-hive - Overrides default mapping from SQL type datatypes to Hive datatypes
```

- **Importing Data into HBase**

```
$ sqoop import --connect --table --username --password --hbase-table

--column-family	- Sets column family for the import
--hbase-create-table - If specified, creates missing HBase tables and fails if already exists
--hbase-row-key	- Specifies which column to use as the row key
--hbase-table - Imports to Hbase table
```

- **Sqoop-Import-all-Tables**


```markdown
The import-all-tables imports all tables in a RDBMS database to HDFS. Data from each table is stored in a separate directory in HDFS. Following conditions must be met in order to use sqoop-import-all-tables:

1. Each table should have a single-column primary key.

2. You should import all columns of each table.

3. You should not use splitting column, and should not check any conditions using where clause.

$ sqoop import-all-tables (generic args) (import args) 
$ sqoop-import-all-tables (generic args) (import args)

Sqoop specific arguments are similar with sqoop-import tool, but few options like --table, --split-by, --columns, and --where arguments are invalid.

$ sqoop-import-all-tables ---connect --username --password 

```
- **Sqoop-Codegen**

```bash
Sqoop-codegen command generates Java class files which encapsulate and interpret imported records. The Java definition of a record is initiated as part of the import process. For example, if Java source is lost, it can be recreated. New versions of a class can be created which use different delimiters between fields, and so on.

$ sqoop codegen (generic args) (codegen args) 
$ sqoop-codegen (generic args) (codegen args)

$ sqoop codegen --connect --table 
```
- **Sqoop-Eval**

```python
Sqoop-eval command allows users to quickly run simple SQL queries against a database and the results are printed on to the  console. 
$ sqoop eval --connect --query "SQL query"
```

- **Sqoop-List-Database**

```
$ sqoop list-databases --connect 
```

- **Sqoop-List-Tables**

```
$ sqoop list-tables –connect 
```

