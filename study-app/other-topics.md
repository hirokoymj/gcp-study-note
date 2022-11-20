### Audit Logs

[Audit Logs: Querying Logs, Pricing and Retention](https://www.youtube.com/watch?v=dVBBKR3SgDQ&t=3s)

Access Control to Audit Logs

| Audit Logs     | Logging.viewer | Logging.privateLogViewer |
| -------------- | -------------- | ------------------------ |
| Admin Activity | Yes            | Yes                      |
| Data Access    | NO             | Yes                      |
| Policy Denied  | Yes            | Yes                      |
| System Event   | Yes            | Yes                      |

### Deployment Manager

[Youtube - Cloud Deployment Manager](https://www.youtube.com/watch?v=gEzlEg-XtsE)

```
gcloud deployment-manager deployments create quickstart-deployment --config vm.yaml
```

```
resources:
- name: vm-created-by-deployment-manager
  type: compute.v1.instance
  properties:
    zone: us-central1-a
    machineType: zones/us-central1-a/machineTypes/n1-standard-1
    disks:
    - deviceName: boot
      type: PERSISTENT
      boot: true
      autoDelete: true
      initializeParams:
        sourceImage: projects/debian-cloud/global/images/family/debian-11
    networkInterfaces:
    - network: global/networks/default
```

**--preview**
Preview the requested create without actually instantiating the underlying resources. (default=False)

**--config=CONFIG**
Filename of a top-level yaml config that specifies resources to deploy. For a guide to creating a configuration, refer to [Creating a Basic Configuration](https://cloud.google.com/deployment-manager/docs/configuration/create-basic-configuration)

References:

- [gcloud deployment-manager deployments create](https://cloud.google.com/sdk/gcloud/reference/deployment-manager/deployments/create#--config)
