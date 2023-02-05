# Run Apache Spark On Amaon Athena 

## Table of contents

- [What's included](#whats-included)
- [Set Up Work](#set-up)
- [Main Tutorial](#main-tutorial)
- [Useful Links](#useful-link)
- [Creators](#creators)

## What's included

The repo is to supplement the [youtube video](https://youtu.be/grfSNj2EMwo) on running Apache Spark Workloads on Athena AWS. 

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
1. Read data from Customers Table using Notebook Using Dyanmic Frame 
    ``` 
    # Read from the customers table in the glue data catalog using a dynamic frame
    dynamicFrameCustomers = glueContext.create_dynamic_frame.from_catalog(
    database = "athena_spark_tutorial_db", 
    table_name = "customers"
    )

    # Show the top 10 rows from the dyanmic dataframe
    dynamicFrameCustomers.show(10)
    ```

2. Check data types in Dynamic Frame 
    ```
    # Check types in dynamic frame
    dynamicFrameCustomers.printSchema()
    ```

3.  Select Fields From A Dynamic frame
    ```
    # Selecting certain fields from a Dyanmic DataFrame
    dyfCustomerSelectFields = dynamicFrameCustomers.select_fields(["customerid", "fullname"])

    # Show top 10
    dyfCustomerSelectFields.show(10)
    ```


## Creators

**Johnny Chivers**

- <https://github.com/johnny-chivers/>

## Useful Links

- [youtube video](https://youtu.be/grfSNj2EMwo) 
- [website](https://www.johnnychivers.co.uk)
- [buy me a coffee](https://www.buymeacoffee.com/johnnychivers)


Enjoy :metal: