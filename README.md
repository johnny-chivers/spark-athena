# Run Apache Spark On Amazon Athena 

## Table of contents

- [What's included](#whats-included)
- [Set Up Work](#set-up)
- [Main Tutorial](#main-tutorial)
- [Useful Links](#useful-link)
- [Creators](#creators)

## What's included

The repo is to supplement the [youtube video](https://youtu.be/yb7dAQl1Di8) on running Apache Spark Workloads on Athena AWS. 

You will need an AWS User that has permissions to access Athena, S3, and the Glue Data Catalog. I am using my Admin account to carry out the tutorial. 

## Data
Below is the schema for the customer table which is created in the Glue Data Catalog by the cloudformation template. The schema also contains some sample data. 

**Customers**
| Customerid      | Firstname | Lastname| Fullname |
| ----------- | ----------- |-----------|-----------|
|  293 | Catherine                | Abel                   | Catherine Abel                 |
|  295 | Kim                      | Abercrombie            | Kim Abercrombie                |
|  297 | Humberto                 | Acevedo                | Humberto Acevedo               |


## Set up

1. Run the cloud formation template. This will create;
- The S3 bucket
- Glue database
- Customers table in the Glue database

2. Upload the data from the `data` folder


## Main Tutorial
1. Show all database 
    ```
    # Show Databases
    spark.sql("show databases").show()
    ```



2. Read data from Customers Table  
    ``` 
    # Read from the customers table in the glue data catalog 
    sqlDF = spark.sql("SELECT * From athena_spark_tutorial_db.customers")
    
    #Show top 50 rows
    sqlDF.show(50)
    ```

2. Print the schema
    ```
    # Check types in frame
    sqlDF.printSchema()
    ```

3.  Select Fields From A  frame
    ```
    # Selecting certain fields from a  DataFrame
    sqlDF = spark.sql("SELECT Firstname From athena_spark_tutorial_db.customers")
    
    #Show top 50 rows
    sqlDF.show(50)
    ```


## Creators

**Johnny Chivers**

- <https://github.com/johnny-chivers/>

## Useful Links

- [youtube video](https://youtu.be/yb7dAQl1Di8) 
- [website](https://www.johnnychivers.co.uk)
- [buy me a coffee](https://www.buymeacoffee.com/johnnychivers)


Enjoy :metal:
