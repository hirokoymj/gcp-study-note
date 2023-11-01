# Deploy an app to a GKE cluster

https://cloud.google.com/kubernetes-engine/docs/deploy-app-cluster

```
gcloud config set project my-gke-demo
```

## Create a GKE cluster

Create an **Autopilot** cluster named hello-cluster:

```
gcloud container clusters create-auto hello-cluster \
 --region=us-west1
```

## Get authentication credentials for the cluster

After creating your cluster, you need to get authentication credentials to interact with the cluster:

```
gcloud container clusters get-credentials hello-cluster \
 --region us-west1
```

## Deploy an application to the cluste

Now that you have created a cluster, you can deploy a containerized application to it

**Create the Deployment**

```
kubectl create deployment hello-server \
    --image=us-docker.pkg.dev/google-samples/containers/gke/hello-app:1.0
```

**Expose the Deployment**

```
kubectl expose deployment hello-server --type LoadBalancer --port 80 --target-port 8080
```

**Inspect and view the application**

```
kubectl get pods
kubectl get service hello-server
http://EXTERNAL_IP
```
