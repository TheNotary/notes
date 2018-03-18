# Apache HBase

Home:  https://hbase.apache.org/

HBase is a database that can be operated ontop of the Hadoop HDFS.  It's considered a part of Hadoop tangentially.


## Idea

The database exists as files on an HDFS volume.  It's non-relational, so object-storage basically?


## Usage

1. Create a table with two 'column famalies' using the below snippet:

```
create '/some/mapr/fs/path/table_name', {NAME=>'addr'}, {NAME=>'order'}
```

An actual file will be created at... `/mapr/some/mapr/fs/path/table_name` containing records

2. Describe an existing table

```
describe '/some/mapr/fs/path/table_name'
```

3. Put in an object

```
put '/some/mapr/fs/path/table_name', 'my_objects_id', 'addr:city', 'Chicago'
```

4. Read an object by its ID

```
get '/some/mapr/fs/path/table_name', 'my_objects_id'
```


5. To dump the rows in a table:

```
scan '/some/mapr/fs/path/table_name'
```
