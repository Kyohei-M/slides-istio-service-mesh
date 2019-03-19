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
### Microservice

- 

---
### Service Mesh

- 

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
### Architecture

<center><img src="https://istio.io/docs/concepts/what-is-istio/arch.svg" width=80%></center>

---
### Architecture

- Envoy

- Mixer

- Pilot

- Citadel

- Galley

---
### Envoy

.right-small[
<center><img src="https://avatars2.githubusercontent.com/u/30125649" width=100%></center>
]

.left-large[
- a high-performance proxy developed in C++

- deployed as a sidecar in the Kubernetes Pod

- add to an existing deployment with no need to rearchitect or rewrite code
]

---
### Envoy Features

- Dynamic service discovery

- Load balancing

- TLS termination

- HTTP/2 and gRPC proxies

- Circuit breakers

---
### Envoy Features

- Health checks

- Staged rollouts with %-based traffic split

- Fault injection

- Rich metrics

---
### 

<center><img src="stackdriver-logs-viewer.png" width=100%></center>

---
class: center, middle, inverse
# Demo

---
### Books

<center><img src="https://images-na.ssl-images-amazon.com/images/I/91VNghpL1EL.jpg" width=45%></center>

---
### Links

[Istio](https://istio.io/)

[Istioサービスメッシュ入門](https://www.slideshare.net/yokawasa/istio-114360124)
