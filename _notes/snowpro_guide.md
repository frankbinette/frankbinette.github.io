---
title: SnowPro Core Study Guide
update_date: 2021-04-09
---

# Snowflake SnoPro Certification Study Guide

This guide is based on the SnowPro [Study Guide](https://snowflakeuniversity.mindtickle.com/#/update/1240380887853059998)

## 1. SNOWFLAKE OVERVIEW & ARCHITECTURE (28%)

### Introduction to Snowflake - Key Concepts & Architecture ([link](https://docs.snowflake.com/en/user-guide/intro-key-concepts.html))

Snowflake is not based on any existing technolgoy - it combines a completely new SQL query engine with an innovative architecture natively designed for the cloud.

#### Data Platform as a Cloud Service

- Snowflake is a true SaaS: no hardware, no software to install, no maintenance to do - all done by Snowflake.
- Snowflake runs completely on public cloud infrastructures.
- Snowflake uses virtual compute instances for its compute needs and a storage service for persistent storage of data. 
- Snowflake cannot be run on private cloud infrastructures (on-premises or hosted).

#### Snowflake Architecture

Snowflake’s architecture is a hybrid of traditional shared-disk and shared-nothing database architectures:
- Uses a central data repository for persisted data that is accessible from all compute nodes in the platform, but
- Processes queries using MPP (massively parallel processing) compute clusters where each node in the cluster stores a portion of the entire data set locally.

![Architecture Image](/blob/snowpro/architecture.png)

Snowflake's architecture consist of 3 layers that scale independently and includes built-in redundancy:

1. Database Storage

- Data is stored into Snowflake internal optimized, compressed, columnar format, with AES-256 encryption.
- Snwoflake manages all aspects of how the data is stored: organization, file size, structure, compression, metadata, statistics, etc.
- Data objects are not directly visible/accessible: must be accessed through SQL queries.

2. Query Processing

- Query execution (compute) is performed in the processing layer in "virtual warehouses".
- Each virtual warehouse hos no impact on the performance of other warehouses, but can access the same data.
- A VH can be scaled up or down for performance.

3. Cloud Services

- A collection of services that coordinate activities across Snowflake and also run on compute instances:
    - Authentication
    - Infrastructure management
    - Metadata management (store)
    - Query parsing, compilation and optimization
    - Access protocol

#### Connecting to Snowflake

Multiple ways to connect to the service:

- A web-based user interface 
- Command line clients (e.g. SnowSQL)
- ODBC and JDBC (to connect from e.g. Tableau)
- Native connectors (e.g. Python Spark)
- Third-party connectors for ETL/BI applications (e.g. Informatica, ThoughtSpot, etc.)

### Snowflake Editions & Deployments ([link](https://snowflakeuniversity.mindtickle.com/#/update/1192528624267286058?series=1186787688786450122))

#### Account Options & Assurances

- Industry Compliance awards: HIPAA, SOC1, SOC2 Type 2, & PCI DSS, FEDRAMP
- Snowflake editions:
    - Standard: A strong balance between features, level of suppoet, and cost.
    - Enterprise: Standard plus 90-day time travel, multi-cluster warehouses, and materialized views.
    - Business Critical: Enterprise plus enhanced security, data protection, and database failover/fallback.
        - E.g. encrypt data transmitted over network within a Virtual Private Cloud (VPC).
- Cloud Platform Providers:
    - AWS
    - GCP
    - Azure
- Deployment Regions:
    - Set by the cloud provider; the availability depends on which one you choose.
- Availability Zones: 
    - Replication of data within a region used to ensure data is always available to end users. It's Snowflake HA on top of Cloud provider HA.
- Multi-Region and Multi-Coud for HA:
    - Replicate your data across multiple regions and clouds.
    - For companies that need to have their data available in more than one region or on more tha one cloud platform.
- Summary:
    - A company can use more than one cloud infrastructure provider by setting up several Snowflake accounts.
    - A company can have its data stored in more than one geographical region by setting up several Snowflake accounts.
    - A company can use a combination of data sharing and replication to distribute data to various regions and cloud platforms.

### Snowflake Pricing & Regions

You should understand the differences between Snowflake Editions, pricing and regions.

#### Snowflake Editions & Pricing ([link](https://www.snowflake.com/pricing/))

![Usage & Pricing Image](/blob/snowpro/pricing-usage.png)

#### Snowflake Regions ([link](https://docs.snowflake.com/en/user-guide/intro-regions.html))

![Regions Image](/blob/snowpro/regions.png)

### Snowflake Architecture

You should understand Snowflake’s unique multi-cluster, shared data and the three distinct layers.

Snowflake’s architecture is a hybrid of traditional shared-disk and shared-nothing database architectures:
- Uses a central data repository for persisted data that is accessible from all compute nodes in the platform, but
- Processes queries using MPP (massively parallel processing) compute clusters where each node in the cluster stores a portion of the entire data set locally.

![Architecture Image](/blob/snowpro/architecture.png)

Snowflake's architecture consist of 3 layers that scale independently and includes built-in redundancy.

#### Database Storage ([link](https://docs.snowflake.com/en/user-guide/intro-key-concepts.html#database-storage))

- Data is stored into Snowflake internal optimized, compressed, columnar format, with AES-256 encryption.
- Snowflake manages all aspects of how the data is stored: organization, file size, structure, compression, metadata, statistics, etc.
- Data objects are not directly visible/accessible: must be accessed through SQL queries.
- Synonyms: Data layer, storage layer

#### Query Processing ([link](https://docs.snowflake.com/en/user-guide/intro-key-concepts.html#query-processing))

- Query execution (compute) is performed in the processing layer in "virtual warehouses".
- Each virtual warehouse hos no impact on the performance of other warehouses, but can access the same data.
- A VH can be scaled up or down for performance.
- Synonyms: Compute layer, virtual warehouse layer, query processing layer.

#### Cloud Services  ([link](https://docs.snowflake.com/en/user-guide/intro-key-concepts.html#cloud-services))

- A collection of services that coordinate activities across Snowflake and also run on compute instances:
    - Authentication
    - Infrastructure management
    - Metadata management (store)
    - Query parsing, compilation and optimization
    - Access protocol
- Query planning, optimization, and compîlation.
- Metadata management, user authentication, metadata storage, data security.
- Synonyms: Cloud services layer, services layer.

### Interface & Connectivity

You should understand a good sense of Snowflake’s WebUI and the Connector Ecosystem.

#### Snwoflake WebInterface (UI) ([link](https://docs.snowflake.com/en/user-guide/connecting.html))

![WebUI URL Image](/blob/snowpro/snow-account.png)

#### SnowSQL (CLI) ([link](https://docs.snowflake.com/en/user-guide/snowsql-use.html))

TO DO

#### Connector Ecosystem ([link](https://docs.snowflake.com/en/user-guide-connecting.html))

TO DO

#### Partner Connector Ecosystem ([link](https://docs.snowflake.com/en/user-guide/ecosystem.html))

Snowflake works with a wide array of industry-leading tools and technologies, enabling you to access Snowflake through an extensive network of connectors, drivers, programming languages, and utilities.

![Partners Connect Image](/blob/snowpro/partners.png)

### Catalog & Objects

#### Database & Schema ([link](https://docs.snowflake.com/en/user-guide/databases.html))

- All data in Snowflake is maintained in databases. 
- Each database consists of one or more schemas, which are logical groupings of database objects, such as tables and views.
- Snowflake does not place any hard limits on the number of databases, schemas (within a database), or objects (within a schema) you can create.

#### Tables ([link](https://docs.snowflake.com/en/user-guide/table-considerations.html))

#### Date/Time data types for columns

- Snowflake recommends using a date or timestamp data type instead of string type:
    - DATE, DATETIME, TIME, TIMESTAMP, TIMETSMAP_LTZ, TIMESTAMP_NTZ, TIMESTAMP_TZ)

Referential integrity constraints

- Referential integrity constraints in Snowflake are informational and, with the exception of NOT NULL, not enforced. Constraints other than NOT NULL are created as disabled.
- Specify a constraint when creating or modifying a table using the CREATE | ALTER TABLE … CONSTRAINT commands.
- Example: 

```sql
create or replace table salespeople (
  sp_id int not null unique,
  name varchar default null,
  region varchar,
  constraint pk_sp_id primary key (sp_id)
);
```
#### When to set a clustering key

- Specifying a clustering key is not necessary for most tables. 
- Snowflake does auto tuning via the optimization engine and micro-partionning.
    - In many cases, micro-partionned by date or timestamp.
- Specify clustering key when:
    - Table is large
    - The order in which the data is loaded does not match the dimension by which it is most commonly queried (e.g. data is loaded by date but reports filter the data by ID).
    - Query Profile indicates that a significant percentage of the total duration time for queries is spent scanning. Queries that filters on one or more specific columns.
- Reclustering rewrites existing data to different order.
    - Previous order is kept 7 days as fail-safe.
    - Costs correlate to the size of the data that is reordered.

#### When to specify column length

- Snowflake compresses column data effectively, therefore, creating columns larger than necessary has minimal impact on the size of data tables.
- Likewise, no query performace difference between a column with maximum length (e.g. `VARCHAR (16777216)`) and a smaller precision.
- If the size of the column is predictable, Snowflake recommends to define appropriate column length:
    - Can help detect issues when loading data.
    - Third-party tools may anticipate consumming the max size thus increase celint-side memory usage.

#### Storing semi-structured data in a VARINAT coumn vs flattening the nested structure

- Store data in VARIANT if not sure what you'll do with it. 
- For better pruning and less storage consumption, fletten your objects if your semi data includes:
    - Dates and timestamps as string values
    - Numbers within strings
    - Arrays
- Use the FLATTEN function to extract the objects and keys you plan to query into a separate table.

#### Converting a permanent table to a transient table or vice-versa

- Currently, it's not possible to change a permanent table to a transient table using ALTER TABLE. Similarly, can't change transient table to permament table.
- Transient property is set at creation and cannot be modified.

Convenrt and copy grants:

```sql
CREATE TRANSIENT TABLE my_new_table LIKE my_old_table COPY GRANTS;
INSERT INTO my_new_table SELECT * FROM my_old_table;
```

Preserve data but not privileges - CREATE TABLE AS SELECT (CTAS):

```sql
CREATE TRANSIENT TABLE my_transient_table AS SELECT * FROM mytable;
```

Can also use clone:

```sql
CREATE TRANSIENT TABLE foo CLONE bar COPY GRANTS;
```

- Old partitions will not be affected (i.e. won’t become transient), but new partitions added to the clone will follow the transient lifecycle.
- Can’t clone a transient table to a permanent table.

#### Views ([link](https://docs.snowflake.com/en/user-guide/views-introduction.html))

What is a view?

- A view allows the result of a query to be accessed as if it were a table. 
- The query is specified in the CREATE VIEW statement.
- Views serve a variety of purposes, including combining, segregating, and protecting data.
- A view can be used almost anywhere that a table can be used (joins, subqueries, etc.). For example, using the views created above:
- A CREATE VIEW command can use a fully-qualified, partly-qualified, or unqualified table name.

```sql
CREATE VIEW doctor_view AS
    SELECT patient_ID, patient_name, diagnosis, treatment FROM hospital_table;

CREATE VIEW accountant_view AS
    SELECT patient_ID, patient_name, billing_address, cost FROM hospital_table;
```

#### Data Types ([link](https://docs.snowflake.com/en/sql-reference/data-types.html))

Snowflake supports most basic SQL data types (with some restrictions) for use in columns, local variables, expressions, parameters, and any other appropriate/suitable locations. Data types are automatically coerced whenever necessary and possible.

Default ones are:

- Numerica: NUMBER & FLOAT
- Strung & Binary: VARCHAR & BINARY
- Logical: BOOLEAN
- Date & Time: DATE & TIMESTAMP
- Semi-structured: VARIANT
- Geographical: GEOGRAPHY

Full list:

![List of Data Types Image](/blob/snowpro/data-types.png)


### Data Sharing

## 2. SNOWFLAKE VIRUAL WAREHOUSES (18%)

### Compute

## 3. SNOWFLAKE STORAGE & PROTECTION (15%)

## 4. DATA MOVEMENT (LOAD & UNLOAD) (14%)

### DATA LOADING

You should understand how to load data (COPY vs INSERT) and Snowflake’s offerings.

Quick facts:

- You can load both strcutured ans semi-structured data into Snowflake.
- The methods for loading data include:
    - Bull loading into Snowflake tables, from local files or external cloud storage.
    - Continuous loading in microbatches with Snowpipe.
    - INSERT INTO tables using SQL (not recommended)
- Stages: Handy built-in cloud directories that are not available in traditional databases. Snowflake uses these types of stages:
    - Internal: Uses a cloud storage location manage by Snowflakeé
    - External: Cloid storage outside of Snowflake (for exmaple, Amazon S3 bucket, Microsoft Azure Blob, Google Cloud bucket, etc.)
- In a load process, data arrives at theese Snowflake object in this sequence: Stage > Pipe > Table

![Ways to Load Data Image](/blob/snowpro/ways-to-load-data.png)

#### Stages, file format, pipe ([link](https://docs.snowflake.com/en/user-guide/intro-summary-loading.html))

**COPY INTO**

Data file details (files used to load data):

- Location of files: 
    - Local environment: files are first staged in a Snowflake stage, then loaded into a bucket.
    - Amazon S3: files can be loaded directly from any S3 bucket.
    - Google Clouyd Storage: files can be loaded directly from any Cloud Storgae container.
    - Microsoft Azure: files can be loaded directly from any Azure container.
- File formats:
    - Delimited files (CSV, TSV, etc. any valid delimited is supported, default is comma)
    - JSON
    - Avro: auto detection when file compressed using Snappy.
    - ORC: auto detection when file compressed using Snappy or zlib.
    - Parquet: auto detection when file compressed using Snappy.
    - XML: supported as a preview feature.
- File encoding:
    - File format-specific:
        - For delimited files the default caracter set is UTF-8
            - To use any other caracter sets you must specify the encoding to use for loading
            - See caracter [list](https://docs.snowflake.com/en/user-guide/intro-summary-loading.html#supported-character-sets-for-delimited-files)
        - For all other file format, the only supported character set is UTF-8

Compression of staged files (how Snowflake handles compression of data files for loading):

- Uncompressed files: 
    - gzip: when staging uncompressed files in Snowflake stage, the files are auto compress using gzip, unless compression is explicitly disabled.
- Already-compressed files:
    - Snowflake can auto detect any of the compression methods or you can explicitly specify the method:
        - gzip
        - bzip2
        - deflate
        - raw_deflate
    - Auto-detection is not yet supported for Brotli-compressed files; when staging or loading these kind you must explicitly specify the compression method
        - Brotli
        - Zstandard

Encryption of staged files (how Snowflake handles encyption of data files for loading)

- Unencrypted files
    - 128-bit or 256-bit keys
    - Files are auto encrypted using 128-bit keys but 256-bit can be neabled (configuration required)
- Already-encrypted files
    - User-supplied key
    - Can be loaded into Snowflake but the key must be provided to Snowflake.

#### Bulk Load using COPY ([link](https://docs.snowflake.com/en/user-guide/data-load-overview.html))

Snowflake refers to the location of data files in cloud storage as a stage. **COPY INTO \<table\>** used for bulk and continuous data load (i.e . Snowpipe) supports cloud storage accounts managaed by your business entity (i.e. external stages) as well as cloud storage contained in your Snowflake account (i.e. internal stages).

**External Stages:**

- Loading from any of the cloud storage services (AWS, GCP, Azure) is supported regardless of the cloud platform that hosts your Snowflake account.
- Upload (i.e. stage) files to your cloud storage account using tools provided by the cloud storage service.
- A named external stage is a database object created in a schema. This object stores the URL to files in cloud storage, the settings used to access the cloud storage account, and convenience settings such as the options that describe the format of staged files.
- Create using the **CREATE STAGE** command.

**Internal Stages:**

- Snowflake maintains the following stage types of account:
    - User:
        - A user satge is allocated to each user for storing files.
        - This tsage type is designed to store files that are managed by a single user but can be loaded into multiple tables.
        - User stages cannot be altered or dropped.
    - Table:
        - A stage table is available for each table created in Snowflake.
        - This tage table is designed to store files that are staged and managed by one or more usersbut only loaded into a single table.
        - Table stages cannot be altered or dropped.
        - Note that table stage is not a separate database object; rather, it's an implicit stage tied to the table itself.
        - A stage table has no grantable privileges of its own.
        - To stage files to a table stage, list the files, query them on the stage, or drop them, you must be the table owner (have the role with the ownership privilege on the table).
    - Named:
        - A named internal stage is a database object created in a schema.
        - This stage type cans tore files that are staged and managed by one or more users and loaded into one or more table.
        - Because named stages are database objects, the ability to crwate, modify, use, or drop them can be controlled using security access control privileges.
        - Create stages using **CREATE STAGE** command.
- Upload files to any of the internal stage types from your local file system using **PUT** command.

**Bulk vs Continuous Loading** 

The best solution depends on the volume of data and the frequency of loading.

Bulk loading using **COPY** command

- Enables loading batches of data from files available in cloud storage, or copying (i.e. staging) data files from a local machineto an internal (i.e. Snowflake) cloud storage location before loading the data into tables using the **COPY** command.
- Compute ressources:
    - Relies on user-provides virtual warehouses which are specified in the COPY statement.
    - Users are required to size the warehouse to accomodate expected loads.
- Supports transforming data while loading:
    - Column reordering
    - Column omission
    - Casts
    - Truncating text string thta exceed colun length

Continuous loading using Snowpipe

- Designed to load small volumes of data (o.e. micro-batches) and incrementally make them available.
- Snowpipe loads data within minutes after file are added to a stage and submitted for ingestion.
- This ensures users have the latest results, as soon as the raw data is available.
- Compute ressources
    - Uses compute ressources provided by Snowflake (i.e. a serverless compute model).
    - The Snowflake-provided resources auto resize and scale up/down as required.
    - Charged and itemized using per-second billing.
    - Data ingestion charged based upon the actual workload.
- Supports simple transforming data while loading:
    - Same as bulk loading
- A data pipeline enbales applying complex transformations to loaded data. This workflow generally leverages Snowpipe to load raw data into staging table, then use a series of table streams and tasks to transform and optimize the new data for analysis.

Loading data from Apache Kafka topics

- The Snowflake connector for Kafka enables users to connect to an Apache kafka server, read data from one or more topic, and load data into Snowflake tables.

Alternatives to loading data

- It's not always necessary to load data into Snowflake before executing queries
- External tables (data lake)
    - External tables enable querying existing data stored in external cloud storage without loading it into Snowflake. 
    - Data sets materialized in Snowflake via materialized views are read-only.
    - Beneficial for account that have large amount of data stored in external cloud storage and only want ot query a portion of the data.
    - Can create materialized views on subset of this data for improved query perf.

#### Loading Consideration & Load Management ([link](https://docs.snowflake.com/en/user-guide/data-load-considerations-load.html))

Options for selecting staged data files

- **COPY** command supports several options for loading data file from stage:
    - By path (internal stages) / prefix (Amazon S3 bucket).
    - Specifying a list of specific files to load:
        - `copy into load1 from @%load1/data1/ files=('test1.csv', 'test2.csv', 'test3.csv')`
        - Providing a discrete list of files is generally the fastest but maximum of 1000 files.
    - Using pattern matching to identify specific files by pattern (using REGEX).
        - `copy into people_data from @%people_data/data1/ pattern='.*person_data[^0-9{1,3}$$].csv'`
        - Slowest but good if you want to load files in the same order.
- These options enables you to copy a fraction of the staged data into Snowflake with a single command.
- Can combine both for further control.
- Concurrent COPY statements that match a subset of files lets you take advantage of parallel oprations.

Execute paralell copy statements that reference the same data files

- When a COPY statement is executed, Snowflake sets a load status in the metadata.
- This prevents parallel COPY to load the same files.
- If one or more cCOPY fail to load, the files become available for subsequent COPY to load.

Loading older files (see [link](https://docs.snowflake.com/en/user-guide/data-load-considerations-load.html#loading-older-files))

JSON data: removing the "null" values

- In a VARIANT column, NULL values are stored as a string, not the SQL NULL.
- If they are in fact "null" set the file format option STRIP_NULL_VALUES to TRUE with the COPY INTO \<table\> command.
- Retaining "null" as a string wastes storage and slow queries.

CSV Data: trimming leading spaces

- Use the TRIM_SPACE file format option to remove undesirable spaces during data load.
- `COPY INTO mytable FROM @%mytable FILE_FORMAT = (TYPE = CSV TRIM_SPACE=true FIELD_OPTIONALLY_ENCLOSED_BY = '0x22');`

#### Continuous Load Options - Snowpipe ([link](https://docs.snowflake.com/en/user-guide/data-load-overview.html))

Same [reference](https://docs.snowflake.com/en/user-guide/data-load-overview.html) as "Bulk Load using COPY".

#### Error handling & Troubleshooting ([link](https://docs.snowflake.com/en/user-guide/ui-history.html))

Using the history page to monitor queries

- The History page allows you to view and drill into the details of all queries executed in the last 14 days.
- The default info:
    - Current status of query: waiting in queue, running, succeeded, failed
    - SQL text of your query
    - Query ID
    - Info on the warehouse used to execute
    - Query start, end time, and duration
    - Info on the query including number of bytes scanned and nu,ber fo rows returned
- Overview of features:
    - Refresh and auto-refresh the History page
    - Show/hide filters (filters are active for current session)
    - Include (or not) client-generated statements
    - Include queries executed by user tasks
    - Abort specific queries
    - Etc.
- Major features:
    - View query details and results (if you have the rights)
    - Export query results
    - View query profile


### DATA UNLOADING

You should understand data can be unloaded from Snowflake to either local storage or cloud storage locations.

#### Unloading data from Snowflake to External Cloud Storage (S3, GCS, Azure Blob) ([link](https://docs.snowflake.com/en/user-guide-data-unload.html))

#### Unloading data from Snowflake to Internal Snowflake Storage ([link](https://docs.snowflake.com/en/user-guide/data-unload-snowflake.html))

![Data Unload Image](/blob/snowpro/data-unload.png)

TO DO

#### Unloading data from Snowflake to Local / Network Drive ([link](https://docs.snowflake.com/en/user-guide/data-unload-considerations.html))

TO DO

#### Data Unloading Considerations

Same link as before...

### SNOWFLAKE CONNECTOR FOR KAFKA

This is only for the SnowPro Advanced Exam. You should understand data can be loaded into Snowflake tables via the Snowflake Connector for Kafka. 

## 5. SNOWFLAKE ACCOUNT & SECURITY (12%)

## 6. SNOWFLAKE PERFORMANCE & TUNING (9%)

## 7. SEMI-STRUCTURED DATA (4%)

You should understand best practices to load and store semi-structured data and the types  supported with Snowflake.

### Different Formats, Variant Table Type ([link](https://docs.snowflake.com/en/user-guide/semistructured-intro.html))

Semi-structured data is data that does not conform to the standards of traditional structured data (no shit!)

The two key features that distinguish semi data are nested data structure and the lack of fixed schema (with n-level hierarchies).

Loading semi-structured data

- The steps are the same a structured data...
- Snowflake load semi data into a VARIANT column.
- Using COPY INTO, you can extract selected columns from a staged data file into separate table column.

Supported file formats:
- JSON: a hierarchical collection of name/value pairs grouped into objects and arrays.
- Avro: 
    - It uses schemas defined in JSON to produce serialized data in a compact binary format.
    - Loaded into a VARIANT column and query like JSON data.
- ORC:
    - Optimized Row Columnar: Hive data (stored in Hadoop).
    - Loaded into a VARIANT column and query like JSON data. Or extract data into separate table using CREATE TABLE AS SELECT.
    - Max length of ORC binary and string column is subject to Snowflake 16 MB limit for VARCHAR data (compressed).
    - Map data is deserialized into an array of objects.
    - Union data is deserialized into a single object.
- Parquet:
    - Compressed columnar data representation (stored in Hadoop).
    - Loaded into a VARIANT column and query like JSON data. Or extract data into separate table using CREATE TABLE AS SELECT.
- XML:
    - Everybody knows Extensible Markup Language
    - In preview feature...

### Native Syntax, Flattening DATA ([link](https://docs.snowflake.com/en/user-guide/table-considerations.html))

#### Date/Time data types for columns

- Snowflake recommends using a date or timestamp data type instead of string type:
    - DATE, DATETIME, TIME, TIMESTAMP, TIMETSMAP_LTZ, TIMESTAMP_NTZ, TIMESTAMP_TZ)

Referential integrity constraints

- Referential integrity constraints in Snowflake are informational and, with the exception of NOT NULL, not enforced. Constraints other than NOT NULL are created as disabled.
- Specify a constraint when creating or modifying a table using the CREATE | ALTER TABLE … CONSTRAINT commands.
- Example: 

```sql
create or replace table salespeople (
  sp_id int not null unique,
  name varchar default null,
  region varchar,
  constraint pk_sp_id primary key (sp_id)
);
```

#### When to set a clustering key

- Specifying a clustering key is not necessary for most tables. 
- Snowflake does auto tuning via the optimization engine and micro-partionning.
    - In many cases, micro-partionned by date or timestamp.
- Specify clustering key when:
    - Table is large
    - The order in which the data is loaded does not match the dimension by which it is most commonly queried (e.g. data is loaded by date but reports filter the data by ID).
    - Query Profile indicates that a significant percentage of the total duration time for queries is spent scanning. Queries that filters on one or more specific columns.
- Reclustering rewrites existing data to different order.
    - Previous order is kept 7 days as fail-safe.
    - Costs correlate to the size of the data that is reordered.

#### When to specify column length

- Snowflake compresses column data effectively, therefore, creating columns larger than necessary has minimal impact on the size of data tables.
- Likewise, no query performace difference between a column with maximum length (e.g. `VARCHAR (16777216)`) and a smaller precision.
- If the size of the column is predictable, Snowflake recommends to define appropriate column length:
    - Can help detect issues when loading data.
    - Third-party tools may anticipate consumming the max size thus increase celint-side memory usage.

#### Storing semi-structured data in a VARINAT coumn vs flattening the nested structure

- Store data in VARIANT if not sure what you'll do with it. 
- For better pruning and less storage consumption, fletten your objects if your semi data includes:
    - Dates and timestamps as string values
    - Numbers within strings
    - Arrays
- Use the FLATTEN function to extract the objects and keys you plan to query into a separate table.

#### Converting a permanent table to a transient table or vice-versa

- Currently, it's not possible to change a permanent table to a transient table using ALTER TABLE. Similarly, can't change transient table to permament table.
- Transient property is set at creation and cannot be modified.

Convenrt and copy grants:

```sql
CREATE TRANSIENT TABLE my_new_table LIKE my_old_table COPY GRANTS;
INSERT INTO my_new_table SELECT * FROM my_old_table;
```

Preserve data but not privileges - CREATE TABLE AS SELECT (CTAS):

```sql
CREATE TRANSIENT TABLE my_transient_table AS SELECT * FROM mytable;
```

Can also use clone:

```sql
CREATE TRANSIENT TABLE foo CLONE bar COPY GRANTS;
```

- Old partitions will not be affected (i.e. won’t become transient), but new partitions added to the clone will follow the transient lifecycle.
- Can’t clone a transient table to a permanent table.
