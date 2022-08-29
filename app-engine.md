# App Engine

- Deploy a website using App Engine with this.
- Standard environment and flexible environment

### Standard vs Flexible - Application instances

| Standard                               | flexible                                                                                    |
| -------------------------------------- | ------------------------------------------------------------------------------------------- |
| pplication instances run in a sandbox, | Application instances run within Docker containers on Compute Engine virtual machines (VM). |

### Standard vs Flexible - language

| Standard                                                     | flexible                                      |
| ------------------------------------------------------------ | --------------------------------------------- |
| **specific versions** of the supported programming languages | Python, Java, Node.js, Go, Ruby, PHP, or .NET |

**Standard Environment**

- Python 2.7, Python 3.7, Python 3.8, Python 3.9, and Python 3.10
- Java 8, Java 11, and Java 17
- Node.js 10, Node.js 12, Node.js 14, Node.js 16
- PHP 5.5, PHP 7.2, PHP 7.3, PHP 7.4, and PHP 8.1
- Ruby 2.5, Ruby 2.6, Ruby 2.7, and Ruby 3.0
- Go 1.11, Go 1.12, Go 1.13, Go 1.14, Go 1.15, and Go 1.16

### Pricing

| Standard                | Flexible                                             |
| ----------------------- | ---------------------------------------------------- |
| Based on instance hours | Based on usage of vCPU, memory, and persistent disks |

## gcloud app deploy

To deploy a single service:

```js
gcloud app deploy ~/my_app/app.yaml
```

To deploy multiple services:

```js
gcloud app deploy service1/app.yaml
gcloud app deploy service2/app.yaml

//or

gcloud app deploy service1/app.yaml service2/app.yaml
```

By default, the service is deployed to the current project configured via:

```js
gcloud config set core/project PROJECT
```

**--promote**

Promote the deployed version to receive all traffic.

**--no-promote**

no traffic received. Use --no-promote flag for testing.

**References:**

- https://cloud.google.com/appengine/docs/the-appengine-environments
- https://cloud.google.com/sdk/gcloud/reference/app/deploy
