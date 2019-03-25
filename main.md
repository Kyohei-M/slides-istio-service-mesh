name: inverse
layout: true
class: center, middle, inverse-red

---
# Istio Service Mesh
# Introduction

---
layout: false
### Assumptions

- Basic knowledge of Kubernetes

### Targets

People who:

- don't know Service Mesh

- have never used Istio

---
### Microservices?

- Loosely coupled

- Independently deployable

- Organized around business capabilities

- Implemented using different programming languages

- Continuous delivery/deployment of large, complex applications

---
### Service Mesh?

Describe the network of microservices that make up applications and the interactions between them

- Service Discovery

- Load Balancing

- Failure Recovery

- Metrics and Monitoring

---
### Service Mesh?

More complex operational requirements

- A/B Testing

- Canary Rollouts

- Rate Limiting

- Access Control

- End-to-end Authentication

---
class: center, middle, red
# What is Istio?

---
### Istio

.right-small[
<center><img src="https://istio.io/img/logo.png" width=100%></center>
]

.left-large[
- Open source independent service mesh

- Deployed as sidecars in the Pods

- CNCF hosted project(Envoy)
]

---
### Istio

Connect, secure, control, and observe services

.left-half[
<center><img src="istio-services-1.png" width=100%></center>
]

.right-half[
<center><img src="istio-services-2.png" width=100%></center>
]

---
### Architecture

<center><img src="https://istio.io/docs/concepts/what-is-istio/arch.svg" width=65%></center>

---
### Architecture

- Data plane

    - Envoy

---
### Architecture

- Control plane

    - Mixer

    - Pilot

    - Citadel

    - Galley

---
### Envoy

A high-performance proxy developed in C++

.right-small[
<center><img src="https://avatars2.githubusercontent.com/u/30125649" width=100%></center>
]

.left-large[
- Deployed as a sidecar in the Kubernetes Pod

- Add to an existing deployment with no need to rearchitect or rewrite code
]

---
### Envoy Features

- Dynamic Service Discovery

- Load Balancing

- TLS Termination

- HTTP/2 and gRPC proxies

- Circuit Breakers

---
### Envoy Features

- Health Checks

- Staged Rollouts with %-based Traffic Split

- Fault Injection

- Rich Metrics

---
### Mixer

A platform-independent component

- Enforces access control and usage policies across the service mesh

- Collects telemetry data from the Envoy proxy and other services

- Includes a flexible plugin model

---
### Pilot

Provides service discovery for:

- Envoy sidecars
    
- Traffic management capabilities for intelligent routing  
(e.g. A/B Tests, Canary Rollouts)
    
- Resiliency  
(e.g. Timeouts, Retries, Circuit Breakers)

---
### Citadel

Strong service-to-service/end-user authentication with built-in identity and credential management

### Galley

Istio’s configuration validation, ingestion, processing and distribution component

---
class: center, middle, red
# Setup using Istio on GKE

---
### Set IAM

Set the default compute service account to include:

- roles/container.admin (Kubernetes Engine Admin)

- Editor (on by default)

---
### Set IAM

<center><img src="https://istio.io/docs/setup/kubernetes/install/platform/gke/dm_gcp_iam_role.png" width=80%></center>

---
### Create a Cluster

- Need 4 nodes

- Check "Enable Istio (beta)" on Advanced options

<center><img src="gcp-create-cluster.png" width=100%></center>

---
### Show Istio Resources

```console
$ kubectl get svc -n istio-system
```

<center><img src="istio-svc.png" width=100%></center>

or

```console
$ kubectl get po -n istio-system
```

---
### Install Istio

1. Go to the [Istio release](https://github.com/istio/istio/releases) page to download the installation file

1. Extract the downloaded installation file

1. Change directory to the root of the Istio installation

1. Add the istioctl client to the PATH:

```console
$ export PATH=$PWD/bin:$PATH
```

---
class: center, middle, red
# Example

---
### Bookinfo

<center><img src="https://istio.io/docs/examples/bookinfo/noistio.svg" width=80%></center>

---
### Bookinfo

4 separate microservices:

- Productpage

- Details

- Reviews

- Ratings

---
### Bookinfo

3 versions of the Reviews microservice:

- Version v1  
doesn’t call the ratings service

- Version v2  
calls the ratings service, and displays black stars

- Version v3  
calls the ratings service, and displays red stars

---
### Deploy

Enable automatic sidecar injection:

```console
$ kubectl label namespace default \
  istio-injection=enabled
```

Deploy the application using kubectl:

```console
$ kubectl apply -f \
  samples/bookinfo/platform/kube/bookinfo.yaml
```

---
### Check

Confirm all services and pods are running:

```console
$ kubectl get po,svc
```

<center><img src="istio-po-svc.png" width=100%></center>

---
### Define Ingress Gateway

```console
$ kubectl apply -f \
  samples/bookinfo/networking/bookinfo-gateway.yaml

$ kubectl get gateway
NAME               AGE
bookinfo-gateway   17s
```

---
### Control Ingress Traffic

Deploy the httpbin service:

```console
$ kubectl apply -f samples/httpbin/httpbin.yaml
```

Set the ingress IP and ports:

```console
$ export INGRESS_HOST=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.status.loadBalancer.ingress[0].ip}')
$ export INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="http2")].port}')
$ export SECURE_INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="https")].port}')
```

---
class: center, middle, red
# Demo

---
### Books

<center><img src="https://images-na.ssl-images-amazon.com/images/I/91VNghpL1EL.jpg" width=45%></center>

---
### Links

[Microservice Architecture](https://microservices.io/index.html)

[Istio](https://istio.io/)

[Istio - Google Cloud](https://cloud.google.com/istio/)

[Istioサービスメッシュ入門](https://www.slideshare.net/yokawasa/istio-114360124)

[Installing Istio on GKE](https://cloud.google.com/istio/docs/istio-on-gke/installing)

[Install Istio on the Google Kubernetes Engine](https://istio.io/docs/setup/kubernetes/install/platform/gke/)

[Bookinfo Application](https://istio.io/docs/examples/bookinfo/)

---
class: center, middle, red
# Thank You!
