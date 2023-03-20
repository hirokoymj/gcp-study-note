# Connect to Cloud SQL for MySQL from Cloud Shell

## MySQL

- [quickStart:MySQL](https://cloud.google.com/sql/docs/mysql/connect-instance-cloud-shell)
- Enable Cloud SQL Admin API
- Note: Cloud Shell doesn't work with a private IP address. These instructions are only for an instance with a public IP address.
- Steps

1. Go to Cloud SQL Instances
2. Create Instance -> MySQL
3. Enter instance ID (myinstance)
4. Enter a password for the root user
5. Create

```
gcloud services enable sqladmin.googleapis.com
gcloud sql connect myinstance --user=root
CREATE DATABASE guestbook;
USE guestbook;
CREATE TABLE entries (guestName VARCHAR(255), content VARCHAR(255),
    entryID INT NOT NULL AUTO_INCREMENT, PRIMARY KEY(entryID));
    INSERT INTO entries (guestName, content) values ("first guest", "I got here!");
    INSERT INTO entries (guestName, content) values ("second guest", "Me too!");
SELECT * FROM entries;
```


## Postgres
- [quickStart:Postgres](https://cloud.google.com/sql/docs/postgres/connect-instance-cloud-shell)
- Enter a password for the postgres user.
- The psql prompt appears.
- https://www.tutorialspoint.com/postgresql/postgresql_create_table.htm

```
gcloud sql connect myinstance --user=postgres
```
