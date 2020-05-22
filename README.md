# Project Overview

This project will introduce you to the core concepts of Apache Airflow. To complete the project, you will need to create your own custom operators to perform tasks such as staging the data, filling the data warehouse, and running checks on the data as the final step.

We have provided you with a project template that takes care of all the imports and provides four empty operators that need to be implemented into functional pieces of a data pipeline. The template also contains a set of tasks that need to be linked to achieve a coherent and sensible data flow within the pipeline.

You'll be provided with a helpers class that contains all the SQL transformations. Thus, you won't need to write the ETL yourselves, but you'll need to execute it with your custom operators.

![Dag](p5_dag.png "Dag diagram")

## Directory Structure

This is the folder structure of the project

```bash
.
├── LICENSE
├── README.md                 ' Project description
├── create_tables.sql         ' Sql file to create the tables in Redshift
├── dags
│   └── udac_example_dag.py   ' Code for the DAG file
└── plugins
    ├── __init__.py           ' Configuration file for Python packages
    ├── helpers
    │   ├── __init__.py       ' Configuration file for Python packages
    │   └── sql_queries.py    ' File containing all the SQL to be executed
    └── operators
        ├── __init__.py       ' Configuration file for Python packages
        ├── data_quality.py   ' Code for data validation operator
        ├── load_dimension.py ' Code for dimension table data load
        ├── load_fact.py      ' Code for fact table data load
        └── stage_redshift.py ' Code for loading S3 blobs into Redshift
```

## Setup

### Prerequisites

1. AWS Account
2. Redshift Cluster

### Instructions

1. create_tables.sql needs to be executed on the Redshift cluster to create the tables.
2. Airflow connections need to be setup to access AWS S3 and AWS Redshift
3. `udac_example_dag.py` needs to be updated with the connection ids for redshift `redshift_conn_id="<Airflow redshift connection id>"` and
`aws_credentials_id="<Airflow AWS credentials id>"`
4. Run the DAG on Airflow