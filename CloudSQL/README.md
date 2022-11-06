# QuickStart: Connect to MySQL instance using Cloud Shell

[Quickstart: Connect to Cloud SQL for MySQL from Cloud Shell](https://cloud.google.com/sql/docs/mysql/connect-instance-cloud-shell)

1. Create a MySQL instance in Cloud console

   - Instance Name: `myinstance`
   - Password for root user

2. Connect to MySQL instance

```
gcloud sql connect myinstance --user=root
```

```
CREATE DATABASE guestbook;
```

```sql
USE guestbook;
CREATE TABLE entries (guestName VARCHAR(255), content VARCHAR(255),
    entryID INT NOT NULL AUTO_INCREMENT, PRIMARY KEY(entryID));
INSERT INTO entries (guestName, content) values ("first guest", "I got here!");
INSERT INTO entries (guestName, content) values ("second guest", "Me too!");
```

```sql
SELECT * FROM entries;
```

```js
+--------------+-------------------+---------+
| guestName    | content           | entryID |
+--------------+-------------------+---------+
| first guest  | I got here!       |       1 |
| second guest | Me too!           |       2 |
+--------------+-------------------+---------+
2 rows in set (0.00 sec)
mysql>
```

**Create MySQL instance**

```
gcloud sql instances create myinstance \
--database-version=MYSQL_8_0 \
--cpu=2 \
--memory=7680MB \
--region=us-central1

gcloud sql connect myinstance --user=root
```

**Create Postgres instance and connect Postgres db**

```
gcloud sql instances create flights \
    --database-version=POSTGRES_13 --cpu=2 --memory=8GiB \
    --region=us-west1 --root-password=Passw0rd

gcloud sql connect flights --user=postgres
```

```
gcloud sql instances create myinstance \
--database-version=MYSQL_8_0 \
--cpu=2 \
--memory=7680MB \
--region=us-central1
```

### Links

https://cloud.google.com/sql/docs/mysql/create-instance#gcloud

<hr />

# Quickstart: Connect from Compute Engine

https://cloud.google.com/sql/docs/mysql/connect-instance-compute-engine

https://cloud.google.com/sql/docs/mysql/connect-compute-engine

