# Little Lemon DataBase
Little Lemon needs to build a robust relational database system in MySQL to store large amounts of data which they can also easily manage and locate as required. 

## Table of Contents 

- [Have you created a GitHub repository to house your code?](#Have_you_created_a_GitHub_repository_to_house_your_code?)
- [Have you generated an ER diagram of the tables in the Little Lemon database?](#Have_you_generated_an_ER_diagram_of_the_tables_in_the_Little_Lemon_database?)
- [Have you implemented a procedure called `GetMaxQuantity()` that returns the maximum quantity in an order?](#Have_you_implemented_a_procedure_called_GetMaxQuantity()_that_returns_the_maximum_quantity_in_an_order?)
- [Have you implemented a procedure called `ManageBooking()`  that manages bookings in the Little Lemon database?](#Have_you_implemented_a_procedure_called_ManageBooking()_that_manages_bookings_in_the_Little_Lemon_database?)
- [Have you implemented the Python client so that you can communicate with your database using Python?](#Have_you_implemented_the_Python_client_so_that_you_can_communicate_with_your_database_using_Python?)
- [Have you implemented a procedure called `UpdateBooking()`  that alters an existing booking in the Little Lemon database?](#Have_you_implemented_a_procedure_called_UpdateBooking()_that_alters_an_existing_booking_in_the_Little_Lemon_database?) 
- [Have you implemented a procedure called `CancelBooking()` that allows you remove bookings from the Little Lemon database?](#Have_you_implemented_a_procedure_called_CancelBooking()_that_allows_you_remove_bookings_from_the_Little_Lemon_database?) 
  
## Have you created a GitHub repository to house your code?

Yes, I have created a repository on GitHub, which serves not only to host the code but also to facilitate collaboration. I am open to contributions and suggestions, and you can find all the necessary information to contribute in the README file. Here is the link to the [repository](https://github.com/diegovillatoromx/Little_Lemon_DataBase/edit/main/README.md)

![diagram](https://github.com/diegovillatoromx/Airflow-Managed-ETL-for-Snowflake-and-AWS-Data/blob/main/data_architecture.png)

## Have you generated an ER diagram of the tables in the Little Lemon database?
 
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

## Have you implemented a procedure called `GetMaxQuantity()` that returns the maximum quantity in an order? 

## Have you implemented a procedure called `ManageBooking()`  that manages bookings in the Little Lemon database?

## Have you implemented the Python client so that you can communicate with your database using Python?

## Have you implemented a procedure called `UpdateBooking()`  that alters an existing booking in the Little Lemon database?

## Have you implemented a procedure called `CancelBooking()` that allows you remove bookings from the Little Lemon database?

