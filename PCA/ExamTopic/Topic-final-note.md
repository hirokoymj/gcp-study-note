# GKE

- Cluster -> Nodes(VM) -> Pod(container), Pod(container), Pod(container) [1]
- a cluster consists of at least one control plane and multiple worker machines called nodes.[1]
- Cluster type: Autopilot and Standard
- To deploy your app to the GKE cluster you created, you need two Kubernetes objects.[3]

| Kubernetes objects | Description                      |
| ------------------ | -------------------------------- |
| Deployment         | to define your app.              |
| Service            | to define how to access your app |

- A deployment is responsible for keeping a set of pods running.
- A service is responsible for enabling network access to a set of pods.

## Deploy an app to a GKE cluster

- https://cloud.google.com/kubernetes-engine/docs/deploy-app-cluster

```
1. Create a GKE cluster
gcloud container clusters create-auto hello-cluster \
    --location=us-central1

2. Get authentication credentials for the cluster
gcloud container clusters get-credentials hello-cluster \
    --location us-central1

3. Create the Deployment
# To run hello-app in your cluster, you need to deploy the application
kubectl create deployment hello-server \
    --image=us-docker.pkg.dev/google-samples/containers/gke/hello-app:1.0

4. Expose the Deployment
# After deploying the application, you need to expose it to the internet so that users can access it.
# You can expose your application by creating a Service.
kubectl expose deployment hello-server \
    --type LoadBalancer \
    --port 80 \
    --target-port 8080

5. Inspect the running Pods.
kubectl get nodes

6. Inspect the hello-server Service
kubectl get service hello-server

7. View the app.
http://EXTERNAL_IP
```

## HelloApp using Node.js

- **Deploy an app to a GKE cluster**
- https://cloud.google.com/kubernetes-engine/docs/deploy-app-cluster

```
1. Create a GKE cluster
gcloud container clusters create-auto hello-cluster \
    --location=us-central1

1. Get authentication credentials for the cluster
gcloud container clusters get-credentials hello-cluster \
    --location us-central1

1. Create the Deployment
# To run hello-app in your cluster, you need to deploy the application
kubectl create deployment hello-server \
    --image=us-docker.pkg.dev/google-samples/containers/gke/hello-app:1.0

1. Expose the Deployment
# After deploying the application, you need to expose it to the internet so that users can access it.
# You can expose your application by creating a Service.
kubectl expose deployment hello-server \
    --type LoadBalancer \
    --port 80 \
    --target-port 8080

1. Inspect the running Pods.
kubectl get nodes

1. Inspect the hello-server Service
kubectl get service hello-server

1. View the app.
http://EXTERNAL_IP
```

1. Node.js Hello App (index.js)
2. Containerizing an app with Cloud Build
   - Dockerfile
   - get Project ID
   - Store your container in Artifact Registry
   - Build your container image using Cloud Build
3. Create a GKE cluster
4. Deploying to GKE using Deployment and Service
   - deployment.yaml
   - service.yaml
5. View the app - http://EXTERNAL_IP

```
gcloud config get-value project

gcloud artifacts repositories create hello-repo \
    --project=PROJECT_ID \
    --repository-format=docker \
    --location=REGION \

gcloud builds submit \
  --tag REGION-docker.pkg.dev/PROJECT_ID/hello-repo/helloworld-gke .

gcloud container clusters create-auto helloworld-gke \
  --region REGION

kubectl get nodes

kubectl apply -f deployment.yaml

kubectl get deployments

NAME               READY   UP-TO-DATE   AVAILABLE   AGE
hello-deployment   1/1     1            1           20s

kubectl get pods

kubectl apply -f service.yaml

kubectl get services
NAME         TYPE           CLUSTER-IP      EXTERNAL-IP     PORT(S)        AGE
hello        LoadBalancer   10.22.222.222   35.111.111.11   80:32341/TCP   1m
kubernetes   ClusterIP      10.22.222.1     <none>          443/TCP        20m

//http://35.111.111.11
```

## GKE Links

1. [Standard cluster architecture](https://cloud.google.com/kubernetes-engine/docs/concepts/cluster-architecture)
2. [Quickstart-1](https://cloud.google.com/kubernetes-engine/docs/deploy-app-cluster)
3. [Quickstart-2](https://cloud.google.com/kubernetes-engine/docs/quickstarts/deploy-app-container-image)
4. [Kubernetes Service vs Deployment](https://matthewpalmer.net/kubernetes-app-developer/articles/service-kubernetes-example-tutorial.html#:~:text=What's%20the%20difference%20between%20a,running%20in%20the%20Kubernetes%20cluster.)
5. [Commands for Cluster](https://cloud.google.com/kubernetes-engine/docs/how-to/managing-clusters)
6. [ClusterIP-NodePort-LB](https://stackoverflow.com/questions/41509439/whats-the-difference-between-clusterip-nodeport-and-loadbalancer-service-types)
7. [Kubernetes Troubleshooting Walkthrough - Pending Pods](https://managedkube.com/kubernetes/k8sbot/troubleshooting/pending/pod/2019/02/22/pending-pod.html)
8. [GKE Sandbox](https://cloud.google.com/kubernetes-engine/docs/how-to/sandbox-pods?hl=en)
9. [Service vs Deployment](https://matthewpalmer.net/kubernetes-app-developer/articles/service-kubernetes-example-tutorial.html#:~:text=What's%20the%20difference%20between%20a,running%20in%20the%20Kubernetes%20cluster.)
