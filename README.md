# raspberry-pi-cluster-lab
3-node Raspberry Pi cluster simulating cloud infrastructure with Kubernetes, storage, and networking

## Overview

This project documents the setup of a 3-node Raspberry Pi cluster designed to simulate a small cloud infrastructure environment.

The cluster is built using Raspberry Pi devices connected through a network switch and configured for remote access and future container orchestration.

---

## Hardware

* 3 × Raspberry Pi 4
* 1 × Network switch
* 1 × 60W USB power supply
* 3 × microSD cards
* 1 × 512GB USB flash drive (storage node)
* Ethernet cables

---

## Network Architecture

Router → Switch → Raspberry Pi Nodes

---

## Node Roles

* **pi-control** → cluster control node (planned)
* **pi-worker** → compute node (planned)
* **pi-storage** → storage and monitoring node (planned)

---

## Setup Progress

### Completed

* Installed Raspberry Pi OS Lite (64-bit)
* Enabled SSH access
* Configured static hostnames:

  * pi-control
  * pi-worker
  * pi-storage
* Connected nodes through a network switch
* Verified SSH connectivity via hostname
* 

### In Progress

* Bringing all nodes online simultaneously
* Assigning final node roles

### Planned

* Kubernetes (k3s) cluster deployment
* Shared storage (NFS)
* Monitoring stack (Prometheus + Grafana)
* Containerized workloads

---

## Access Method

SSH access is configured for all nodes:

```
ssh pi@<hostname>.local
```

Example:
```
ssh [pi@pi-storage.local](mailto:pi@pi-storage.local)
```

---

## Purpose

This lab is designed to build hands-on experience with:

* Linux system administration
* Networked infrastructure
* Distributed systems
* Container orchestration (planned)
* Cloud architecture concepts

---

## Author

Built as part of a personal cloud engineering learning lab.
