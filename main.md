name: inverse
layout: true
class: center, middle, inverse

---
# Istioで学ぶ
# サービスメッシュ

---
layout: false
### Assumptions

- Kubernetesの基本知識

### Targets

- サービスメッシュ未経験者
- Istio 未経験者

---
### Microservices

- Loosely coupled

- Independently deployable

- Organized around business capabilities

- Implemented using different programming languages

- Continuous delivery/deployment of large, complex applications

---
### Service Mesh

Describe the network of microservices that make up applications and the interactions between them

- Service Discovery

- Load Balancing

- Failure Recovery

- Metrics and Monitoring

---
### Service Mesh

More complex operational requirements

- A/B Testing

- Canary Rollouts

- Rate Limiting

- Access Control

- End-to-end Authentication

---
class: center, middle, inverse
# Istio

---
### Istio

.right-small[
<center><img src="https://istio.io/img/logo.png" width=100%></center>
]

.left-large[
- OSS のサービスメッシュ

- Pod 内にプロキシを配置

- CNCF がホスト(Envoy)
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

- Envoy

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

Provides service discovery for...

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
class: center, middle, inverse
# Demo

---
### Books

<center><img src="https://images-na.ssl-images-amazon.com/images/I/91VNghpL1EL.jpg" width=45%></center>

---
### Links

[Microservice Architecture](https://microservices.io/index.html)

[Istio](https://istio.io/)

[Istioサービスメッシュ入門](https://www.slideshare.net/yokawasa/istio-114360124)
