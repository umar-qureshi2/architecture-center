---
title: 
description: 
author: zoinerTejada
ms:date: 01/17/2018
---

# Relational data 

Relational data is data modeled using the relational model, whereby all data is expressed as tuples, and sets of tuples with the same headings form relations. A data store that organizes data using the relational model is referred to as a relational database. Relational databases use a tabular structure to materialize the relational model - that is they expose all the data as rows (tuples) in tables (relations). The database schema defines the columns (headings) of each table. Each column is defined with a name and a data type for all values stored in that column across all rows in the table.

![Example showing data using a relational database](./images/example-relational.png)

Most relational databases use the Structured Query Language (SQL) language that enables a  declarative approach to querying. The query author focuses solely on authoring a query that shapes the desired result, allowing the relational database engine to decide how to actually execute the query. This is as opposed to the procedural approach used by other data stores, whereby the query program specifies the processing steps explicitly.  

Relational databases support varying forms of constraints, including:
- Primary key fields that are used to uniquely identify rows within a table.
- Foreign key fields that are used in one table to refer to a row in another table by referencing the primary key of other table. Foreign keys are used in maintaining referential integrity, ensuring that the referenced rows are not altered or deleted while the referencing row depends on them.
- Primary indexes are being used by the primary key to define the order of the data as it sits on disk.
- Secondary indexes provide an alternative combination of fields by which to quickly locate the desired rows, without having to re-sort the entire data on disk. The index structure used by relational databases typically includes B+ trees, R-trees and bitmaps. 
- Entity integrity contraints that use expressions to define constraints that limit the values that can be stored within a single column, or in relationship to values in other columns of the same row.

- Primary key and unique constraints, that are used to uniquely identify rows within a table.
- Foreign key constraints that are created on a table to reference a row in another table by referencing the primary key or alternate key of the other table. Foreign key constraints are used in maintaining referential integrity, disallowing changes that would result in a mismatch in foreign key column values between referenced and referencing tables.
- Primary and secondary indexes. Primary indexes, which are used by the primary key, define the order of the data as it sits on disk. Secondary indexes provide an alternative combination of fields by which to quickly locate the desired rows, without having to re-sort the entire data on disk. The index structure used by relational databases typically includes B+ trees, R-trees and bitmaps.
- Check constraints, also known as entity integrity constraints, use expressions to define constraints that limit the values that can be stored within a single column, or in relationship to values in other columns of the same row.

Additionally, relational databases allow for the storage of executable code routines in the form of stored procedures and functions, which enable a mixture of declarative and procedural approaches.

## Transactional data 

Transactional data is information an organization collects that tracks the interactions related to what the organization does. These interactions are typically business transactions such as payments received from customers or payments made to suppliers, products moving through inventory, orders taken or services delivered. Transactional events, which represent the transactions themselves, not reference tables, typically contain a time dimension, some numerical values, and references to other data.

Transactional data stores that support strong consistency can leverage transactions using various locking strategies, such as pessimistic locking, to ensure all data are strongly consistent within the context of the enterprise, for all users and processes.

The most common deployment architecture that utilizes transactional data is the data store tier in a 3-tier architecture. A 3-tier architecture typically consists of a presentation tier, business logic tier, and data store tier. A related deployment architecture is the [N-tier](/azure/architecture/guide/architecture-styles/n-tier) architecture, which may have multiple middle-tiers handling business logic.

![Example of a 3-tier application](./images/three-tier-application.png)

### Typical Traits
Transactional data tends to have the following traits:

| Requirement | Description |
| --- | --- |
| Normalization | Highly normalized |
| Schema | Schema on write, strongly enforced|
| Consistency | Strong consistency, ACID guarantees |
| Integrity | High integrity |
| Uses transactions | Yes |
| Locking strategy | Pessimistic or Optimistic|
| Updateable | Yes |
| Appendable | Yes |
| Workload | Heavy writes, moderate reads |
| Indexing | Primary and secondary indexes |
| Datum size | Small to medium sized |
| Model | Relational |
| Data shape | Tabular |
| Query flexibility | Highly flexible |
| Scale | Small (MBs) to Large (a few TBs) | <!--I know it looks weird, but these are plural, not possessive or contractions.-->


## Semantic modeling

A semantic data model is a conceptual model that describes the meaning of the data elements it contains. To put it another way, organizations have their own terms they use for things, sometimes with synonyms, or even different meanings for two different terms. An example of this is where an inventory database tracks a piece of equipment with an asset Id and a serial number, but a sales database might refer to the serial number as the asset Id. There would be no simple way to relate these values without some model that can describe the relationship. This is where semantic modeling can help. It makes it easier for end users to query data by providing a level of abstraction, making it so they do not need to know the underlying data structure and how aggregates and joins are formed. Also, usually columns are renamed to more business user-friendly names, helping users better understand the context and meaning of the data.

Semantic modeling is predominately used for read heavy scenarios, such as analytics and business intelligence (OLAP), as opposed to more write heavy transactional data processing (OLTP). This is mostly due to the nature of a typical semantic layer, where aggregation behaviors are set so reporting tools display them properly, business logic and calculations are defined, time-oriented calculations are included, and oftentimes data is pre-integrated for users (integrated from multiple sources). Traditionally, the semantic layer is placed over top of a data warehouse for these reasons.

![Example diagram of a semantic layer between a data warehouse and a reporting tool](./images/semantic-modeling.png)

There are two primary types of semantic models:

* **Tabular**: Uses relational modeling constructs (model, tables, columns). Internally, metadata is inherited from OLAP modeling constructs (cubes, dimensions, measures). Code and script use OLAP metadata.
* **Multidimensional**: Leverages traditional OLAP modeling constructs (cubes, dimensions, measures).

Relevant Azure service:
- [Azure Analysis Services](https://azure.microsoft.com/services/analysis-services/)


### Example use case

Your organization has data stored in a large database that you want to make available to business users and customers to create their own reports and do some analysis. You can give your users this ability by giving them access to your database. Of course, there are several drawbacks to doing this, not the least of which is managing security on your production database for the users. Also, the design of your database, including the names of tables and columns may not be easy for a user to understand. They would need to know which tables to query, how those tables should be joined, and other business logic that needs to be applied to get the correct results. They would also need to know a query language like SQL to even get started. Most often this will lead to multiple users reporting the same metrics but with different results.

Another option is to encapsulate all the information needed into a semantic model that can be more easily queried by those users with a reporting tool of their choice. The data provided by the semantic model is pulled from a data warehouse, ensuring all users will see a single version of the truth. The semantic model will also provide friendly table and column names, relationships between tables, descriptions, calculations, and row level security.


### Typical Traits

Semantic modeling and analytical processing tends to have the following traits:

| Requirement | Description |
| --- | --- |
| Normalization | Highly normalized |
| Schema | Schema on write, strongly enforced|
| Uses Transactions | No |
| Locking Strategy | None |
| Updateable | No (typically requires recomputing cube) |
| Appendable | No (typically requires recomputing cube) |
| Workload | Heavy reads, read-only |
| Indexing | Multidimensional indexing |
| Datum size | Small to medium sized |
| Model | Multidimensional |
| Data shape:| Cube or star/snowflake schema |
| Query flexibility | Highly flexible |
| Scale: | Large (10s-100s GBs) |


## Where to go from here
Read next: [Transactional Data Common Architecture](./relational-data.md#transactional-data)

See also:

Related common architectures
- [Transactional Data](./relational-data.md#transactional-data)
- [Semantic Modeling](./relational-data.md#semantic-modeling)

Alternative common architectures
- [Non-relational and No-SQL common architectures](./non-relational-data.md)

Related pipeline patterns 

- Working with transactional data
    - [Online Transaction Processing (OLTP)](../pipeline-patterns/online-transaction-processing.md)
    - [Online Analytical Processing (OLAP)](../pipeline-patterns/online-analytical-processing.md)
    - [Data Warehousing](../pipeline-patterns/data-warehousing.md)

Related technology choices
- Transactional data stores
    - [Online Transaction Processing (OLTP) data stores](../technology-choices/oltp-data-stores.md)
    - [Online Analytical Processing (OLAP) data stores](../technology-choices/olap-data-stores.md)
    - [Data Warehouses](../technology-choices/data-warehouses.md)