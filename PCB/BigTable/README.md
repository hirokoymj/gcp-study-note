# Creating and Populating a Bigtable Instance

- Create a Bigtable instance and a Bigtable table with column families.
- Use a Dataflow template to load SequenceFile files from Cloud Storage into Bigtable.
- Verify the data loaded into Bigtable.
- Delete the Bigtable table and instance.

## Task 1. Create a Bigtable instance

- Console

## Task 2. Create a new Bigtable table

- Console

## Task 3. Load data files from Cloud Storage using a Dataflow template

- Console

## Task 4. Verify data loaded into Bigtable

- To connect to Bigtable using cbt CLI commands, you first need to update the .cbtrc configuration file with your project ID and your Bigtable instance ID using Cloud Shell.

```
echo project = `gcloud config get-value project`  >> ~/.cbtrc

echo instance = personalized-sales  >> ~/.cbtrc

cat ~/.cbtrc
project = <project-id>
instance = personalized-sales

//To see the data for the first ten rows of the table
cbt read UserSessions count=10
```

## Task 5. Delete a Bigtable table and instance

- Console

![](./q1.png)

![](./q1a.png)

![](./q2.png)
