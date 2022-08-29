# App Engine

- Deploy a website using App Engine with this.
- Build your application in Node.js, Java, Ruby, C#, Go, Python, or PHP.
- standard and flexible

## standard environment

- Application instances run in a sandbox
- Python, Java, Node.js, PHP, Ruby, Go
- Based on instance hours

## flexible environment

- Application instances run within Docker containers on Compute Engine virtual machines (VM).
- Python, Java, Node.js, Go, Ruby, PHP, or .NET
- Based on usage of vCPU, memory, and persistent disks

## Compare the flexible environment to Compute Engine

- The flexible environment VM instances are restarted on a weekly basis.
- By default, SSH access to the VM instances in the flexible environment is disabled.

## gcloud app deploy

To deploy a single service, run:

```js
gcloud app deploy ~/my_app/app.yaml
```

By default, the service is deployed to the current project configured via:

```js
gcloud config set core/project PROJECT
```

Promote the deployed version to receive all traffic. Overrides the default app/promote_by_default property value for this command invocation. Use --no-promote to disable.

```js
--promote;
--no - promote;
```

**References:**

- https://cloud.google.com/appengine/docs/the-appengine-environments
- https://cloud.google.com/sdk/gcloud/reference/app/deploy
