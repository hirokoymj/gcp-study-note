# VM Startup script

**App Engine Overview**

- https://cloud.google.com/appengine

**App Engine Flexible Environment Overview**

- This doc gives an overview of GAE Flex and is helpful to understand basic features.
- https://cloud.google.com/appengine/docs/flexible

**Choosing an App Engine environment**

- This doc explains the differences between GAE Standard and GAE Flex and is helpful to understand basic features.

**Flexible environment pricing**

- In this doc, you'll learn how GAE Flex usage is charged.
- https://cloud.google.com/appengine/pricing#flexible-environment-pricing

## Structuring Web Services in App Engine

- This page helps you understand how to structure the services and related resources of your app for App Engine.
- [Structuring web services in App Engine](https://cloud.google.com/appengine/docs/flexible/configuration-files)
- [Microservices (Instagram API Live Demo) - Episode 1.4 | Google Cloud ~ App Engine](https://www.youtube.com/watch?v=HCHXZAowMQg&list=PL42xwJRIG3xCtmOrJAQFR5sIJFKIJ9MEn&index=6)

  - 06:22 - start coding
  - 12:08 - app.yaml
  - 13:11 - deploy
  - 17:03 - two services

- [An Overview of App Engine](https://cloud.google.com/appengine/docs/legacy/standard/python/an-overview-of-app-engine#components_of_an_application)

![](modules_hierarchy.svg)

## Handling Requests

- This doc describes how your App Engine application receives requests and sends responses.
- [How requests are handled](https://cloud.google.com/appengine/docs/flexible/how-requests-are-handled?tab=node.js#top)

**Handling requests**

```
const express = require('express');

const app = express();

app.get('/', (req, res) => {
  res.status(200).send('Hello, world!').end();
});

// Start the server
const PORT = parseInt(process.env.PORT) || 8080;
app.listen(PORT, () => {
  console.log(`App listening on port ${PORT}`);
  console.log('Press Ctrl+C to quit.');
});
```

**Handling asynchronous background work**

- For long-running jobs, we recommend using Cloud Tasks. With Cloud Tasks, HTTP requests are long-lived and return a response only after any asynchronous work ends.

**Routing Requests**

- This page describes how HTTP requests from users reach the appropriate version of a service.
- https://cloud.google.com/appengine/docs/flexible/how-requests-are-routed

**Overview of App Security**

- This page describes features to ensure that your App Engine app is secure.
- https://cloud.google.com/appengine/docs/flexible/application-security

**Writing and Viewing Logs**

- This page describes the logs that are available for App Engine apps, and how to write and view log entries.
- https://cloud.google.com/appengine/docs/flexible/writing-application-logs?tab=node.js

**Serving Static Files**

- The page explains how to serve static files in GAE Flex.
- https://cloud.google.com/appengine/docs/flexible/serving-static-files?tab=node.js

**Authenticating Users**

- The page provides basic ideas for user authentication.
- https://cloud.google.com/appengine/docs/flexible/authenticating-users

**Mapping Custom Domains**

- The page illustrates necessary steps to set up a custom domain.
- https://cloud.google.com/appengine/docs/flexible/mapping-custom-domains

**Securing Custom Domains with SSL**

- The page help you use and set up SSL certs for your custom domain.
- https://cloud.google.com/appengine/docs/flexible/securing-custom-domains-with-ssl

## GAE Flex Quickstarts (Node.js)

- Going through this quickstart will help you grasp the basic features and deployment process.
- [Create a Node.js app in the App Engine flexible environment](https://cloud.google.com/appengine/docs/flexible/nodejs/create-app)

## [Lab] Qwiklabs

- [Node.js Google Cloud Storage sample for Google App Engine](https://github.com/GoogleCloudPlatform/nodejs-docs-samples/tree/main/appengine/storage/flexible)

## Configuring your App with app.yaml

- This doc explains how to customize resource, health-check, and scaling settings. Adjust these parameters and get familiar with resource settings.
- [app.yaml Configuration File](https://cloud.google.com/appengine/docs/flexible/reference/app-yaml?tab=node.js#top)
- [Configuring your app with app.yaml - Node.js](https://cloud.google.com/appengine/docs/flexible/nodejs/configuring-your-app-with-app-yaml)

**app.yaml example**

- This sample incurs costs to run on the App Engine flexible environment.
- The settings below are to reduce costs during testing.

```
runtime: nodejs
env: flex
manual_scaling:
  instances: 1
resources:
  cpu: 1
  memory_gb: 0.5
  disk_size_gb: 10
```

```
gcloud app deploy service-name-app.yaml
gcloud app deploy app.flexible.yaml
```

**Automatic scaling**

The default is automatic scaling.

```
automatic_scaling:
  min_num_instances: 1
  max_num_instances: 15
  cool_down_period_sec: 180
  cpu_utilization:
    target_utilization: 0.6
  target_concurrent_requests: 100
```

- min_num_instances

  > The minimum number of instances given to your service. When a service is deployed, it is given this many instances and scales according to traffic. Must be 1 or greater, default is 2 to reduce latency.

- max_num_instances
  > The maximum number of instances that your service can scale up to. The maximum number of instances in your project is limited by your project's resource quota. Default is 20.

**Manual scaling**

```
manual_scaling:
  instances: 5
```

**Controlling Access with Firewalls**

- This doc explains how customers can manage user access based on IPs. Read through the page, and try "Creating firewall rules" section.
- https://cloud.google.com/appengine/docs/flexible/creating-firewalls

**App Engine Flex || Kubernetes Engine — ? - Google Cloud - Community - Medium**

- This article will help you understand similarities and differences with GAE Flex and GKE, with example logs and screenshots.
- https://medium.com/google-cloud/app-engine-flex-container-engine-946fbc2fe00a

**Building Custom Runtimes**

- This doc explains how to create a custom runtime and deploy it in GAE Flex.
- https://cloud.google.com/appengine/docs/flexible/custom-runtimes/build
