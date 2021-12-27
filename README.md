# Project Data pipeline

## Goals
Imaginary music app company, Spotify, was impressed by my former project that was offered from them, which was ETL pipeline to their data warehouse(Amazon Redshift) using app's data to analyze the usage of the app based on data of song that was played as a fact data and data of various app's attribute as dimensional data to slice the fact data in order to get insight, and they want to continue to hire me. Wanting to polish the great to my workpiece, the following task that they gave was to add automation of the ETL process and ability to monitor and to backfill which means the ability to analyze with past data.


## Airflow concept
Airflow has very useful and strong features as below.

1. Web Interface - A UI control dashboard for users and maintainers.
2. Scheduler - Orchestrates the execution of jobs on a trigger or schedule.
3.  Work Queue - Used by the scheduler to deliver tasks that need to be run to the workers.
4. Worker Processes - The tasks are defined in the Directed Acyclic Graph (DAG). When the worker completes a task, it will reference the queue to process more work until no further work remains.
5. Database - Stores the workflow's metadata but not the data produced from the workflow itself, e.g. credentials, connections, history, and configuration.


## Datasets
Here are the S3 links for datasets used in this project:

- Log data: `s3://udacity-dend/log_data `
- Song data: `s3://udacity-dend/song_data`


## Structure of this project
Here are the descriptions of the files:

- `create_tables.py`: SQL create table statements provided with template.

- `udac_example_dag.py`: Defines main DAG, tasks and link the tasks in required order.

- `stage_redshift.py`: Defines StageToRedshiftOperator to copy JSON data from S3 to staging tables in the Redshift via copy command.
- `load_dimension.py`: Defines LoadDimensionOperator to load a dimension table from staging tables.
- `load_fact.py`: Defines LoadFactOperator to load fact table from staging tables.
- d`ata_quality.py`: Defines DataQualityOperator to run data quality checks on all tables passed as parameter.
- `sql_queries.py`: Contains SQL queries for the ETL pipeline, provided in template.


## Config
1. Setup Apache Airflow server
2. Input the AWS credential to Airflow
2. Setup AWS Redshift cluster
3. Input the connection ID of Redshift to Airflow