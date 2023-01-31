# VM Startup script

**Links:**

-[6. Running Startup Scripts in VMs | Google Cloud Quick Tutorials](https://www.youtube.com/watch?v=IYYg4ogb4k0&list=PLuJRcdtonlDAN73rZsRk_eiJ0NU9h1Cms&index=8)

- https://github.com/drehnstrom/space-invaders

startup script

```
#! /bin/bash

apt update
apt install -y git apache2
cd /var/www/html
rm index.html -f
git init
git pull https://github.com/drehnstrom/space-invaders
```

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


**Structuring Web Services in App Engine**
- This page helps you understand how to structure the services and related resources of your app for App Engine.
- https://cloud.google.com/appengine/docs/flexible/configuration-files


**Handling Requests**
- This doc describes how your App Engine application receives requests and sends responses.
- https://cloud.google.com/appengine/docs/flexible/how-requests-are-handled?tab=python


**Routing Requests**
- This page describes how HTTP requests from users reach the appropriate version of a service.
- https://cloud.google.com/appengine/docs/flexible/how-requests-are-routed

Overview of App Security

- This page describes features to ensure that your App Engine app is secure.
- https://cloud.google.com/appengine/docs/flexible/application-security


Writing and Viewing Logs
- This page describes the logs that are available for App Engine apps, and how to write and view log entries.
- https://cloud.google.com/appengine/docs/flexible/writing-application-logs?tab=node.js


**Serving Static Files**
- The page explains how to serve static files in GAE Flex.
- https://cloud.google.com/appengine/docs/flexible/serving-static-files?tab=node.js


Authenticating Users
The page provides basic ideas for user authentication.
https://cloud.google.com/appengine/docs/flexible/authenticating-users


**Mapping Custom Domains**
The page illustrates necessary steps to set up a custom domain.
https://cloud.google.com/appengine/docs/flexible/mapping-custom-domains


**Securing Custom Domains with SSL**
- The page help you use and set up SSL certs for your custom domain.
- https://cloud.google.com/appengine/docs/flexible/securing-custom-domains-with-ssl

**GAE Flex Quickstarts (Python)**
Going through this quickstart will help you grasp the basic features and deployment process.

https://cloud.google.com/appengine/docs/flexible/python/create-app


GAE Flex Quickstarts (Java)
Going through this quickstart will help you grasp the basic features and deployment process.
https://cloud.google.com/appengine/docs/flexible/java/create-app

[Lab] Deploying a Python Flask Web Application to App Engine Flexible | Qwiklabs
https://partner.cloudskillsboost.google/focuses/13499?catalog_rank=%7B%22rank%22%3A1%2C%22num_filters%22%3A0%2C%22has_search%22%3Atrue%7D&parent=catalog&search_id=7249279



**Configuring your App with app.yaml**
- This doc explains how to customize resource, health-check, and scaling settings. Adjust these parameters and get familiar with resource settings.
https://cloud.google.com/appengine/docs/flexible/custom-runtimes/configuring-your-app-with-app-yaml



Controlling Access with Firewalls
This doc explains how customers can manage user access based on IPs. Read through the page, and try "Creating firewall rules" section.
https://cloud.google.com/appengine/docs/flexible/creating-firewalls


**App Engine Flex || Kubernetes Engine — ? - Google Cloud - Community - Medium**
- This article will help you understand similarities and differences with GAE Flex and GKE, with example logs and screenshots.
https://medium.com/google-cloud/app-engine-flex-container-engine-946fbc2fe00a



**Building Custom Runtimes**
This doc explains how to create a custom runtime and deploy it in GAE Flex.
https://cloud.google.com/appengine/docs/flexible/custom-runtimes/build


