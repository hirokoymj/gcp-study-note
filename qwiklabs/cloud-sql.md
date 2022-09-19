## Create a Cloud SQL database

1. Create a MySQL instance
2. Machine Type - Standard 1 vCPU, 3.75 GB, Storage: HDD/SSD, Connection: Checked Private and Public
3. Create a database
4. Connection string: gentle-keyword-362802:asia-northeast1:wordpress-db
5. Private IP: 10.29.224.3
6. (Public IP: 34.85.89.206)

## Task 2. Configure a proxy on a virtual machine

```js
// Download the Cloud Proxy and make it executable
wget https://dl.google.com/cloudsql/cloud_sql_proxy.linux.amd64 -O cloud_sql_proxy && chmod +x cloud_sql_proxy
export SQL_CONNECTION=gentle-keyword-362802:asia-northeast1:wordpress-db
// Connection string: gentle-keyword-362802:asia-northeast1:wordpress-db
// To activate the proxy connection to your Cloud SQL database
./cloud_sql_proxy -instances=$SQL_CONNECTION=tcp:3306 &

// Listening on 127.0.0.1:3306 for [SQL_CONNECTION_NAME]
//Ready for new connections
```

## Download and install the Cloud SQL Auth proxy

**Mac M1**

```js
// Download the Cloud SQL Auth proxy:
curl -o cloud_sql_proxy https://dl.google.com/cloudsql/cloud_sql_proxy.darwin.arm64

//The Cloud SQL Auth proxy executable
chmod +x cloud_sql_proxy
```

- https://cloud.google.com/sql/docs/mysql/sql-proxy#mac-m1

## Task 3. Connect an application to the Cloud SQL instance

```js
curl -H "Metadata-Flavor: Google" http://169.254.169.254/computeMetadata/v1/instance/network-interfaces/0/access-configs/0/external-ip && echo
```

## Wordpress VM Instances

### wordpress-private-ip

- private IP: 10.142.0.2
- public IP: 34.74.70.98
- URL: http://34.74.70.98
- MySQL: 10.29.224.3(MySQL Private IP)

> Note: Notice that wordpress-private-ip is located at us-central1, where your Cloud SQL is located, which enables you to leverage a more secure connection.

### wordpress-proxy

- private IP: 10.142.0.3
- public IP: 34.148.2.174
- URL: http://34.148.2.174
- MySQL Host: 127.0.0.1

  > You are using 127.0.0.1, localhost as the Database IP because the proxy you initiated listens on this address and redirects that traffic to your SQL server securely.
