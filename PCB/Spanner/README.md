# Cloud Spanner - Database Fundamentals

## Overview

- Cloud Spanner is Google’s fully managed, horizontally scalable relational database service.
- Customers in financial services, gaming, retail

## Task 1. Create an instance

- Databases -> Spanner

## Task 2. Create a database

- From the instance details page, click Create database.

## Task 3. Create a table in your database

- On the Database Details page for your banking-db database, click Create table.

```
CREATE TABLE Customer (
  CustomerId STRING(36) NOT NULL,
  Name STRING(MAX) NOT NULL,
  Location STRING(MAX) NOT NULL,
) PRIMARY KEY (CustomerId);
```

## Task 4. Insert and modify data

- banking-db database -> Customer table -> Data -> Query

```
INSERT INTO
  Customer (CustomerId,
    Name,
    Location)
VALUES
  ('bdaaaa97-1b4b-4e58-b4ad-84030de92235',
    'Richard Nelson',
    'Ada Ohio'
    );
```

## Task 5. Use the Google Cloud CLI with Cloud Spanner

- Create an instance

```
gcloud spanner instances create banking-instance-2 \
--config=regional-us-central1  \
--description="Banking Instance 2" \
--nodes=2
```

- List an instance

```
gcloud spanner instances list
```

- Creating a database

```
gcloud spanner databases create banking-db-2 --instance=banking-instance-2
```

- Reduce nodes from 2 to 1

```
gcloud spanner instances update banking-instance-2 --nodes=1
```

## Task 6. Use Automation Tools with Cloud Spanner

- Terraform

# Cloud Spanner - Loading Data and Performing Backups

## Task 1. Explore the instance

- Database -> Spanner -> Instance -> Customer database -> Query
- No result at this point.

## Task 2. Insert data with DML

```
gcloud spanner databases execute-sql banking-db --instance=banking-instance \
 --sql="INSERT INTO Customer (CustomerId, Name, Location) VALUES ('bdaaaa97-1b4b-4e58-b4ad-84030de92235', 'Richard Nelson', 'Ada Ohio')"
```

## Task 3. Insert data through a client library

- https://cloud.google.com/spanner/docs/getting-started/nodejs#write-data

```js
const { Spanner } = require("@google-cloud/spanner");

/**
 * TODO(developer): Uncomment the following lines before running the sample.
 */
// const projectId = 'my-project-id';
// const instanceId = 'my-instance';
// const databaseId = 'my-database';

// Creates a client
const spanner = new Spanner({
  projectId: projectId,
});

// Gets a reference to a Cloud Spanner instance and database
const instance = spanner.instance(instanceId);
const database = instance.database(databaseId);

database.runTransaction(async (err, transaction) => {
  if (err) {
    console.error(err);
    return;
  }
  try {
    const [rowCount] = await transaction.runUpdate({
      sql: `INSERT Singers (SingerId, FirstName, LastName) VALUES
      (12, 'Melissa', 'Garcia'),
      (13, 'Russell', 'Morales'),
      (14, 'Jacqueline', 'Long'),
      (15, 'Dylan', 'Shaw')`,
    });
    console.log(`${rowCount} records inserted.`);
    await transaction.commit();
  } catch (err) {
    console.error("ERROR:", err);
  } finally {
    // Close the database when finished.
    database.close();
  }
});
```

## Task 4. Insert batch data through a client library

## Task 5. Load data using Dataflow

- Dataflow is a Google Cloud service for streaming and batch data processing at large scale.
- Analytics -> Dataflow
- transform data from its origin (sources) to its destination (sinks).

- you will load data into Spanner banking database from a CSV file with over 150,000 rows.
- **Text Files on Cloud Storage to Cloud Spanner** template.
- The manifest file specifies the table, name and type of the columns (in the order that they appear in the CSV file), and the CSV file itself, which is also stored in a Google Cloud Storage bucket.

- The manifest file must be stored in a Google Cloud Storage bucket that Dataflow can access to and read from. For this lab, this is the content of manifest.json:

  ```js
  {
    "tables": [
      {
        "table_name": "Customer",
        "file_patterns": [
            "gs://cloud-training/OCBL372/Customer_List.csv"
        ],
        "columns": [
            {"column_name" : "CustomerId", "type_name" : "STRING" },
            {"column_name" : "Name", "type_name" : "STRING" },
            {"column_name" : "Location", "type_name" : "STRING" }
        ]
      }
    ]
  }
  ```

## Task 6. Backup your database

- Select Backup/Restore on the left menu of the Spanner banking-instance overview page.

# Deploy a Modern Web App connected to a Cloud Spanner Instance

- https://github.com/GoogleCloudPlatform/training-data-analyst/tree/master/courses/cloud-spanner/omegatrade

# Create and Manage Cloud Spanner Databases: Challenge Lab

## Task 1. Create a Cloud Spanner instance

```
gcloud spanner instances create banking-ops-instance \
--config=regional-us-central1  \
--description="Sample Instance" \
--nodes=1
```

## Task 2. Create a Cloud Spanner database

```
gcloud spanner databases create banking-ops-db \
--instance=my-sample-instance
```

## Task 3. Create tables in your database

- Table: Portfolio

```
CREATE TABLE Portfolio (
  PortfolioId	INT64 NOT NULL,
  Name	STRING(MAX),
  ShortName	STRING(MAX),
  PortfolioInfo	STRING(MAX)
) PRIMARY KEY (PortfolioId);
```

- Table: Category

```
CREATE TABLE Category (
  CategoryId INT64 NOT NULL,
  PortfolioId INT64 NOT NULL,
  CategoryName STRING(MAX),
  PortfolioInfo STRING(MAX)
) PRIMARY KEY (CategoryId);
```

- Table: Product

```
CREATE TABLE Product (
  ProductId	INT64 NOT NULL,
  CategoryId	INT64 NOT NULL,
  PortfolioId	INT64 NOT NULL,
  ProductName	STRING(MAX),
  ProductAssetCode	STRING(25),
  ProductClass	STRING(25)
) PRIMARY KEY (ProductId);
```

- Table: Customer

```
CREATE TABLE Customer (
  CustomerId	STRING(36) NOT NULL,
  Name	STRING(MAX) NOT NULL,
  Location	STRING(MAX) NOT NULL
) PRIMARY KEY (CustomerId);
```

## Task 4. Load simple datasets into tables

- Table: Portfolio

```
INSERT INTO
Portfolio (PortfolioId, Name, ShortName, PortfolioInfo)
VALUES
(1, "Banking", "Bnkg", "All Banking Business"),
(2, "Asset Growth", "AsstGrwth", "All Asset Focused Products"),
(3, "Insurance", "Insurance", "All Insurance Focused Products");
```

- Table: Category

```
INSERT INTO
Category (CategoryId, PortfolioId, CategoryName, PortfolioInfo)
VALUES
(1,1,"Cash"),
(2,2,"Investments - Short Return"),
(3,2,"Annuities"),
(4,3,"Life Insurance");
```

- Table: Product

```
INSERT INTO
  Product (ProductId, CategoryId, PortfolioId, ProductName, ProductAssetCode, ProductClass)
VALUES
  (1,1,1,"Checking Account","ChkAcct","Banking LOB"),
  (2,2,2,"Mutual Fund Consumer Goods","MFundCG","Investment LOB"),
  (3,3,2,"Annuity Early Retirement","AnnuFixed","Investment LOB"),
  (4,4,3,"Term Life Insurance","TermLife","Insurance LOB"),
  (5,1,1,"Savings Account","SavAcct","Banking LOB"),
  (6,1,1,"Personal Loan","PersLn","Banking LOB"),
  (7,1,1,"Auto Loan","AutLn","Banking LOB"),
  (8,4,3,"Permanent Life Insurance","PermLife","Insurance LOB"),
  (9,2,2,"US Savings Bonds","USSavBond","Investment LOB");
```

## Task 5. Load a complex dataset

**Prepare Dataflow**

```
nano manifest.json
```

```js
{
    "tables": [
        {
            "table_name": "Customer",
            "file_patterns": [
                "gs://cloud-training/OCBL375/Customer_List_500.csv"
            ],
            "columns": [
                {"column_name" : "CustomerId", "type_name" : "STRING" },
                {"column_name" : "Name", "type_name" : "STRING" },
                {"column_name" : "Location", "type_name" : "STRING" }
            ]
        }
    ]
}
```

**Create a bucket to upload manifest.json file**

```
gsutil mb gs://Project ID
gsutil cp manifest.json gs://Project ID/
```

**Enable APIs**

```
gcloud services disable dataflow.googleapis.com --force
gcloud services enable dataflow.googleapis.com
```

**Dataflow**

- Job name: spanner-load
- us-west1
- template: Text Files on Cloud Storage to Cloud
- Cloud Spanner Instance id: banking-ops-instance
- Cloud Spanner database id: banking-ops-db
- Manifest file: gs://Project ID/manifest.json
- Temporary location: gs://Project ID/temp

**Check Customer table in Spanner**

- Spanner -> Instance -> Database -> Customer -> QUery

```sql
select count(*) from Customer;
```

## Task 6. Add a new column to an existing table

- Table -> Category -> Click on Write DDL

  ```
  ALTER TABLE Category ADD COLUMN MarketingBudget INT64;
  ```

- or use gcloud command

  ```
  gcloud spanner databases ddl update banking-ops-db \
  --instance=banking-ops-instance \
  --ddl='ALTER TABLE Category ADD COLUMN MarketingBudget INT64;'
  ```
