# Little_Lemon_DataBase
Little Lemon needs to build a robust relational database system in MySQL to store large amounts of data which they can also easily manage and locate as required. 

## Table of Contents 

- [Have you created a GitHub repository to house your code?](#description)
- [Have you generated an ER diagram of the tables in the Little Lemon database?](#architecture)
- [Have you implemented a procedure called GetMaxQuantity() that returns the maximum quantity in an order?](#Dataset)
- [Have you implemented a procedure called ManageBooking()  that manages bookings in the Little Lemon database?](#modular-code-overview)
- [Methodology](#Methodology)
- [Contribution](#contribution) 
- [Contact](#contact) 
  
## Architecture

The Snowflake database architecture blends elements of traditional shared-disk and shared-nothing designs. It features a centralized data repository, akin to shared-disk architectures, ensuring universal access across all compute nodes. Snowflake enhances query performance through Massively Parallel Processing (MPP) compute clusters. Each node within the cluster locally stores a segment of the complete dataset, mirroring the principles of shared-nothing architectures. This approach harmonizes the simplicity of shared-disk designs with the speed and scalability inherent in shared-nothing architectures. 

![diagram](https://github.com/diegovillatoromx/Airflow-Managed-ETL-for-Snowflake-and-AWS-Data/blob/main/data_architecture.png)

## Modular Code Overview
 
```terminal
kinesis_snowflake_data_pipeline/
├── src/
│   ├── ec2_logs_emitter/
│   │   ├── customer_data.py
│   │   ├── order_data.py
├── infrastructure/
│   ├── create_s3_bucket.sh
│   ├── setup_iam_role.sh
│   ├── create_ec2_instance.sh
│   ├── create_kinesis_firehose_delivery.sh
│   ├── install_kinesis_agent.sh
│   ├── move_data_to_firehose_delivery.sh
│   ├── setup_snowflake.sh
│   ├── create_airflow_dag.sh
│   ├── mwaa_setup/
│   │   ├── create_mwaa_environment.sh
│   │   ├── add_snowflake_connection.sh
├── config/
│   ├── s3_bucket_config.json
│   ├── iam_role_config.json
│   ├── ec2_instance_config.json
│   ├── kinesis_firehose_delivery.json
│   ├── kinesis_agent_config.json
│   ├── snowflake_config.json
│   ├── airflow_dag_config.json
│   ├── mwaa_config/
│   │   ├── mwaa_environment_config.json
│   │   ├── snowflake_connection_config.json
├── data/
│   ├── landing_zone/
│   ├── processing_zone/
│   ├── processed_zone/
│   ├── customer/
│   │   ├── customer_data_file.txt
│   ├── order/
│   │   ├── order_data_file.txt
├── scripts/
│   ├── upload_data_to_landing.sh
│   ├── trigger_airflow_dag.sh
│   ├── load_data_to_snowflake.sh
│   ├── transform_data_in_snowflake.sh
│   ├── transfer_data_between_zones.sh
├── images/
│   ├── kinesis_logo.png
│   ├── airflow_logo.png
│   ├── snowflake_logo.png
├── README.md

```
