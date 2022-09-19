## Create a bucket and Access Control Lists (ACLs)

- Name: unique name
- Location type: Multi-Enforce public access prevention on this bucket: unchecked
- Access control: Fine-grained (object-level permission in addition to your bucket-level permissions)

```js
// Download a sample file and make two copies
export BUCKET_NAME_1=<enter bucket name 1 here>
echo $BUCKET_NAME_1

// Download a file
curl \
https://hadoop.apache.org/docs/current/\
hadoop-project-dist/hadoop-common/\
ClusterSetup.html > setup.html

// Make two copies
cp setup.html setup2.html
cp setup.html setup3.html

// Copy the file to the bucket
gsutil cp setup.html gs://$BUCKET_NAME_1/

// Get the default access list for setup.html
gsutil acl get gs://$BUCKET_NAME_1/setup.html  > acl.txt
cat acl.txt

// Set the access list to private and verify the result
gsutil acl set private gs://$BUCKET_NAME_1/setup.html
gsutil acl get gs://$BUCKET_NAME_1/setup.html  > acl2.txt
cat acl2.txt

// Update the access list to make the file readable
gsutil acl ch -u AllUsers:R gs://$BUCKET_NAME_1/setup.html
gsutil acl get gs://$BUCKET_NAME_1/setup.html  > acl3.txt
cat acl3.txt
```

## Customer-supplied encryption keys (CSEK)

```js
python3 -c 'import base64; import os; print(base64.encodebytes(os.urandom(32)))'
//tmxElCaabWvJqR7uXEWQF39DhWTcDvChzuCmpHe6sb0=
ls -al
nano .boto
// if .boto file is empty, generate .boto file using the gsutil config -n command
// Modify .boto file
//Before:
//# encryption_key=
//After:
//encryption_key=tmxElCaabWvJqR7uXEWQF39DhWTcDvChzuCmpHe6sb0=

gsutil cp setup2.html gs://$BUCKET_NAME_1/
gsutil cp setup3.html gs://$BUCKET_NAME_1/

// Return to the Cloud Console
// Both setup2.html and setup3.html files show that they are customer-encrypted.
```

## Enable lifecycle management

```js
// View lifecycle policy
gsutil lifecycle get gs://$BUCKET_NAME_1
// Create a JSON lifecycle policy file
nano life.json
{
  "rule":
  [
    {
      "action": {"type": "Delete"},
      "condition": {"age": 31}
    }
  ]
}
// Set lifecycle policy
gsutil lifecycle set life.json gs://$BUCKET_NAME_1
// View and check lifecycle policy
gsutil lifecycle get gs://$BUCKET_NAME_1
```

## Enable versinoing

```js
gsutil versioning get gs://$BUCKET_NAME_1
// the Suspended policy means that it is not enabled.

// Enable versioning
gsutil versioning set on gs://$BUCKET_NAME_1

// Verify versioning
gsutil versioning get gs://$BUCKET_NAME_1

ls -al setup.html

//Delete any 5 lines from setup.html to change the size of the file.
nano setup.html

//Copy the file to the bucket with the -v versioning option:
gsutil cp -v setup.html gs://$BUCKET_NAME_1

nano setup.html

//Delete another 5 lines
gsutil cp -v setup.html gs://$BUCKET_NAME_1

// List all versioning of the file
gsutil ls -a gs://$BUCKET_NAME_1/setup.html
```

## Cross-project sharing

1. (proj #1)Create a bucket
2. (proj #1)Create Service Account

   > Name: cross-project-storage, JSON Key download, credentials.json

3. (proj #1) Storage Object Viewer
4. (proj #2) Create a VM
5. (proj #2) Open SSH

```js
export BUCKET_NAME_2=myproj-qwiklabs-gcp-12345
export FILE_NAME="Screen Shot 123.png"
gsutil ls gs://$BUCKET_NAME_2/
//AccessDeniedException: 403 404513585876-compute@developer.gserviceaccount.com does not have storage.objects.list access to the Google Cloud Storage bucket.
```

6. (proj #2) Upload credentials.json to authorize the through the SSH terminal

   ```js
   ls
   //credentials.json
   // To authorize the VM to use the Google Cloud API
   gcloud auth activate-service-account --key-file credentials.json


   gsutil ls gs://$BUCKET_NAME_2/
   // VISIBLE the file
   gs://myproj-qwiklabs-gcp-12345/Screen Shot 123.png
   ```

7. (proj #1) Change Storage Object View to Storage Object Admin so you can modify the file

## Make a nested directory and sync with a bucket

```js
// Make a nested folder and copy the file
mkdir firstlevel
mkdir ./firstlevel/secondlevel
cp setup.html firstlevel
cp setup.html firstlevel/secondlevel

//Sync the firstlevel directory
gsutil rsync -r ./firstlevel
gs://$BUCKET_NAME_1/firstlevel

// Check it the file exists in the first level folder /firstlevel.
gsutil ls -r gs://$BUCKET_NAME_1/firstlevel
```
