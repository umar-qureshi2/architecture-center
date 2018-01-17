# Extract, transform, load (ETL)

Capture web application logs and custom telemetry with [Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview), and create, schedule, and manage your ETL data pipeline using [Azure Data Factory](https://docs.microsoft.com/en-us/azure/data-factory/). Deploy your SSIS packages to Azure--with the [Azure-SSIS integration runtime](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure) (IR) in Azure Data Factory--to apply data transformation as a step in the ETL pipeline, before loading the transformed data into [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/).

![ETL](./images/implementation-example_etl.png)

## Highlighted services

* [Azure Data Factory](https://docs.microsoft.com/en-us/azure/data-factory/)
* [Azure-SSIS integration runtime](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure)
* [Azure Storage blobs](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction)
* [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/)
* [Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview)

## In this guide

* Common Data Architectures
    * [Data pipeline](./common-architectures/data-pipeline.md)
    * [Relational data](./common-architectures/relational-data.md)
* Pipeline Patterns
    * [Online Transaction Processing (OLTP)](./pipeline-patterns/online-transaction-processing.md)
    * [Monitoring data solutions](./pipeline-patterns/monitoring-data-solutions.md)
* Technology Choices
    * [Options for pipeline orchestration, control flow, and data movement](./technology-choices/pipeline-orchestration-data-movement.md)
    * [Data ingest](./technology-choices/data-ingest.md)
