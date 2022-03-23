# Service to manage configuration data (service-config-data)

[![GitHub release](https://img.shields.io/github/release/lj020326/service-config-data.svg)](https://github.com/lj020326/service-config-data/releases)
[![GitHub issues](https://img.shields.io/github/issues/lj020326/service-config-data.svg)](https://github.com/lj020326/service-config-data/issues)
[![GitHub commits](https://img.shields.io/github/commits-since/lj020326/service-config-data/0.0.1.svg)](https://github.com/lj020326/service-config-data)

[![Build Status](https://travis-ci.org/lj020326/service-config-data.svg?branch=master)](https://travis-ci.org/lj020326/service-config-data)
[![GitHub Issues](https://img.shields.io/github/issues/lj020326/service-config-data.svg)](https://github.com/lj020326/service-config-data/issues)
[![Average time to resolve an issue](http://isitmaintained.com/badge/resolution/lj020326/service-config-data.svg)](http://isitmaintained.com/project/lj020326/service-config-data "Average time to resolve an issue")
[![Percentage of issues still open](http://isitmaintained.com/badge/open/lj020326/service-config-data.svg)](http://isitmaintained.com/project/lj020326/service-config-data "Percentage of issues still open")
[![Docker Stars](https://img.shields.io/docker/stars/lj020326/service-config-data.svg)](https://hub.docker.com/r/lj020326/service-config-data/)
[![Docker Pulls](https://img.shields.io/docker/pulls/lj020326/service-config-data.svg)](https://hub.docker.com/r/lj020326/service-config-data/)

[![Docker Build Status](https://img.shields.io/docker/build/lj020326/service-config-data)](https://hub.docker.com/r/lj020326/service-config-data/builds/)

[![Codacy Badge](https://api.codacy.com/project/badge/Grade/1818748c6ba745ce97bb43ab6dbbfd2c)](https://www.codacy.com/app/lj020326/service-config-data?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=lj020326/service-config-data&amp;utm_campaign=Badge_Grade)


The `service-config-data` service designed to provide configuration management capabilities across all components. This common service can be used by any application, component or module within permitted boundaries. In it's present implementation, the service allows retrieval of values based on provided key and specified environment (`dev`, `stg`, `prod`, etc.).

---

## Directory structure

This is how complete directory structure should look like after installing all repos and resolving dependancies.

```
├── config-data
│   ├── README.md
│   ├── cassandra.json
│   ├── jhub-whitelist.json
│   ├── jhub_kernels.json
│   ├── k8s-cluster.json
│   ├── service-config-data.json
│   ├── service-scada-load.json
│   ├── services.json
│   └── test.json
├── pkg
│   ├── darwin_amd64
│   │   └── github.com
│   │       └── tidwall
│   │           └── gjson.a
│   └── dep
│       └── sources
└── service-config-data
    ├── JenkinsPod.yaml
    ├── Jenkinsfile
    ├── Makefile
    ├── README.md
    ├── SECURITY.md
    ├── charts
    │   └── service-config
    │       ├── Chart.yaml
    │       ├── requirements.yaml
    │       ├── templates
    │       │   ├── deployment.yaml
    │       │   ├── image-pull-secret.yaml
    │       │   └── service.yaml
    │       └── values-template.yaml
    ├── config.json
    ├── glide.lock
    ├── glide.yaml
    ├── service.go
    ├── skaffold.yaml
    ├── src
    │   ├── config-data-util
    │   │   ├── config_structs.go
    │   │   ├── data_utility.go
    │   │   ├── environment
    │   │   │   └── environment.go
    │   │   ├── kernel
    │   │   │   ├── kernel.go
    │   │   │   └── kernel_test.go
    │   │   ├── key
    │   │   │   └── key.go
    │   │   ├── memfilesystem
    │   │   │   └── memfilesystem.go
    │   │   └── user
    │   │       ├── user.go
    │   │       └── user_test.go
    │   ├── github.com
    │   │   ├── lj020326
    │   │   │   └── service-common-lib
    │   │   │       ├── LICENSE
    │   │   │       ├── Makefile
    │   │   │       ├── README.md
    │   │   │       ├── common
    │   │   │       │   ├── circuitbreaker
    │   │   │       │   │   └── circuitbreaker.go
    │   │   │       │   ├── config
    │   │   │       │   │   ├── config.go
    │   │   │       │   │   └── git.go
    │   │   │       │   ├── logging
    │   │   │       │   │   └── logging.go
    │   │   │       │   └── util
    │   │   │       │       └── util.go
    │   │   │       ├── docker
    │   │   │       │   └── Dockerfile.goservice.template
    │   │   │       └── service
    │   │   │           ├── router.go
    │   │   │           ├── routes.go
    │   │   │           └── webserver.go
    │   │   ├── subosito
    │   │   │   └── gotenv
    │   │   │       ├── CHANGELOG.md
    │   │   │       ├── LICENSE
    │   │   │       ├── README.md
    │   │   │       ├── fixtures
    │   │   │       │   ├── bom.env
    │   │   │       │   ├── exported.env
    │   │   │       │   ├── plain.env
    │   │   │       │   ├── quoted.env
    │   │   │       │   └── yaml.env
    │   │   │       ├── go.mod
    │   │   │       ├── go.sum
    │   │   │       ├── gotenv.go
    │   │   │       └── gotenv_test.go
    │   │   └── tidwall
    │   │       ├── gjson
    │   │       │   ├── LICENSE
    │   │       │   ├── README.md
    │   │       │   ├── SYNTAX.md
    │   │       │   ├── gjson.go
    │   │       │   ├── gjson_gae.go
    │   │       │   ├── gjson_ngae.go
    │   │       │   ├── gjson_test.go
    │   │       │   ├── go.mod
    │   │       │   ├── go.sum
    │   │       │   └── logo.png
    │   │       ├── match
    │   │       │   ├── LICENSE
    │   │       │   ├── README.md
    │   │       │   ├── match.go
    │   │       │   └── match_test.go
    │   │       └── pretty
    │   │           ├── LICENSE
    │   │           ├── README.md
    │   │           ├── pretty.go
    │   │           └── pretty_test.go
    │   ├── gitutil
    │   │   ├── git_utility.go
    │   │   ├── git_utility_test.go
    │   │   └── test_data
    │   │       ├── kernels
    │   │       │   └── spark-kernel-12CPU-24GB
    │   │       ├── sandbox_whitelist.json
    │   │       ├── test_object_storage.json
    │   │       ├── test_users1.json
    │   │       ├── test_users2.json
    │   │       └── user.json
    │   ├── handlers
    │   │   ├── confEnvHandler.go
    │   │   ├── gitHandler.go
    │   │   ├── kernelHandler.go
    │   │   ├── keyHandler.go
    │   │   ├── userHandler.go
    │   │   └── userHandler_test.go
    │   └── helpers
    │       └── helpers.go
    ├── vars-gcp.mk
    ├── vars.mk
    └── watch.sh
```
---

## How to deploy Config Service

### Setup configuration backend Git repo

The very first part of setting up and deploying configuration data service is to setup git-based backend to host actual configurations.

- create Git repository `config-data` (as an example https://github.com/lj020326/config-data.git )
(whether you make it private or public, is entirely up to you)
- create branch called `sandbox`
- check into branch `sandbox` file with the name `test.json`
- edit `test.json` as follows

```
{
  "hello": "world"
}
```

Note - do not merge the branches!

### Deployment on local laptop:

Install main package and dependancies :

```
git clone https://github.com/lj020326/service-config-data.git
cd service-config-data
```

Setup GOPATH:

```
echo $GOPATH
export GOPATH=$GOPATH:$PWD
echo $GOPATH
```

Make sure all dependancies are installed

```
make deps
```

Build `service-config-data` service binaries:

```
make build
```

To get service to run on your local machine (make sure docker is running):

```
make run
```

Now, test if the service runs correctly - open new terminal window and run:

```
 curl http://localhost:8000/api/v2/test/sandbox/hello
```

Service API allows optional parameter specifying the output format. For instance, to get config data in JSON format, run:

```
 curl http://localhost:8000/api/v2/test/sandbox/hello?out=json
```




### Deployment of GCP:

The following environment variables must be set as part of `vars-gcp.mk` in order for service to compile and run properly:

`vars-gcp.mk` file

```
REPO?=github.com/lj020326/config-data
GITACCOUNT?=
APITOKEN?=
CONFIGFILE?=services
REGISTRY?=lj020326
```

Initialize GCP environment:

```
gcloud auth login
```

List available kubernetes clusters:

```
gcloud container clusters list
```

Example of output:

```
NAME                      LOCATION       MASTER_VERSION  MASTER_IP      MACHINE_TYPE   NODE_VERSION   NUM_NODES  STATUS
cluster-services-sandbox  us-central1-a  1.13.7-gke.19   00.000.000.00  n1-standard-1  1.13.7-gke.19  3          RUNNING
```

Than, create `tiller` service account and cluster binding:

```
kubectl create serviceaccount --namespace kube-system tiller
kubectl create clusterrolebinding tiller-cluster-rule --clusterrole=cluster-admin --serviceaccount=kube-system:tiller
```

And, finally, initialize Helm:

```
helm init --service-account tiller --upgrade
```

Last step to build service binaries, create image, push image to docker repo and deploy Helm chart:

```
cd service-config-data
make push
make deploy
```

Once, above steps are done, run following command to list all k8s services deployed in `default` namespace:

```
$ kubectl get services
NAME                  TYPE           CLUSTER-IP   EXTERNAL-IP      PORT(S)          AGE
kubernetes            ClusterIP      10.12.0.1    <none>           443/TCP          4d16h
service-config-data   LoadBalancer   10.12.14.8   xxx.xxx.xxx.xx   8000:30956/TCP   10h
```

You should see public IP for service `service-config-data` - `xxx.xxx.xxx.xx`.

And, finally, to test service deployment, run quick test curl call:

```
$ curl http://xxx.xxx.xxx.xx/api/v2/test/sandbox/hello

world
```

Clean up:

```
make deployclean
```

---
## How to use config service


### 1. `config-data` repository

Consider an example of configuration file `config-data/k8s-cluster.json` in branch `sandbox`, that looks like this

```
{
  "name" : "jx-sandbox",
  "k8s-name" : "k8s-sandbox",
  "apps": [
    {
      "name" : "jenkins",
      "app-type" : "devops"
    },
    {
      "name" : "grafana",
      "app-type" : "devops"
    },
    {
      "name" : "cassandra",
      "app-type" : "storage"
    }
  ],
  "env" : "sandbox",
  "region" : "us-east",
  "git-org" : "",
  "kubectl-ver" : "v1.13.0",
  "helm-ver": "v2.1.3",
  "docker-ver" : "1.12.6",
  "cloud-provider":{
    "name": "ibmcloud",
    "api-endpoint" : "https://api.us-east.bluemix.net"
  }
}
```

Assuming running config service container locally (http://localhost:8000)


### 2. A few use cases of `service-config-data` service

Hope these examples are self explanatory.

```
$ curl http://localhost:8000/api/v2/k8s-cluster/sandbox/region

us-east
```

```
$ curl http://localhost:8000/api/v2/k8s-cluster/sandbox/apps

[
  {
    "name" : "jenkins",
    "app-type" : "devops"
  },
  {
    "name" : "grafana",
    "app-type" : "devops"
  },
  {
    "name" : "cassandra",
    "app-type" : "storage"
  }
]
```

```
$ curl http://localhost:8000/api/v2/k8s-cluster/sandbox/apps.@

3
```

```
$ curl http://localhost:8000/api/v2/k8s-cluster/sandbox/apps.2

{      "name" : "cassandra",      "app-type" : "storage"    }
```

```
$ curl http://localhost:8000/api/v2/k8s-cluster/sandbox/apps.@.name

["jenkins","grafana","cassandra"]
```

```
$ curl http://localhost:8000/api/v2/k8s-cluster/sandbox/apps.1.name

["grafana"]
```

```
$ curl http://localhost:8000/api/v2/k8s-cluster/sandbox/apps.@(name=="cassandra").app-type

storage
```

```
$ curl http://localhost:8000/api/v2/k8s-cluster/sandbox/apps.@(app-type=="devops")@.name

["jenkins","grafana"]
```


---

## Manual step-by-step deployment

### Build service runtime from Go code

```
make build
```

### Build image and push to registry

```
make push
```

### Deploy service

```
make deploy
```

### Clean up

```
make deployclean
```


# Deploy service on Kubernetes cluster using Helm chart

Make sure values file `./service-config/values.yaml` is populated based on template `../service-common-lib/docker/values-template.yaml`

If you're having trouble understanding what values should be in `values.yaml`, refer to `Makefile` - it generates `values.yaml` in section `deploy`

Deploy service by executing the following

```
cd service-config-data/charts
helm upgrade --install config-service --values ./service-config/values.yaml --namespace default  ./service-config/
```

...and clean up:

```
helm del --purge config-service
```


---
