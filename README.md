# Raspberry Pi Cloud Lab

## Overview

This project documents the design and implementation of a 3-node Raspberry Pi homelab built to simulate a small cloud infrastructure environment. The lab was designed to provide hands-on experience with Linux administration, Kubernetes, shared storage, monitoring, and troubleshooting across multiple networked nodes.

The environment includes a Kubernetes control plane, a worker node for running workloads, and a dedicated storage node that provides NFS-backed persistent storage. Monitoring and observability were added using Prometheus, Node Exporter, and Grafana.

This project was built as part of a hands-on cloud engineering learning path and is intended to demonstrate practical infrastructure skills in a home environment.

---

## Objectives

- Build a multi-node Raspberry Pi infrastructure cluster
- Deploy lightweight Kubernetes using k3s
- Configure persistent shared storage using NFS
- Deploy and expose containerized workloads
- Implement observability using Prometheus and Grafana
- Configure alerting for basic node health conditions
- Document architecture, deployment steps, and troubleshooting

---

## Hardware

- 3 × Raspberry Pi 4
- 1 × Raspberry Pi cluster rack
- 1 × network switch
- 1 × 60W multi-port power supply
- 3 × microSD cards
- 1 × 512GB SanDisk USB flash drive
- Ethernet cables
- Existing home router and Wi-Fi network

---

## Node Roles

| Node Name | Role | Purpose |
|---|---|---|
| `pi-control` | Kubernetes control plane | Manages the cluster and Kubernetes resources |
| `pi-worker` | Kubernetes worker node | Runs application workloads |
| `pi-storage` | Storage node | Hosts NFS-backed persistent storage and monitoring endpoint |

---

## Current Architecture

```text
                    Home Router
                         |
                       Switch
          -----------------------------------
          |                |                |
     pi-control       pi-worker        pi-storage
   Kubernetes CP     Workloads         NFS Storage
          |                |                |
          |--------- Prometheus ----------->|
          |                |
          |------------- Grafana -----------|
