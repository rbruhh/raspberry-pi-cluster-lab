# Raspberry Pi Cloud Lab + AI Lead Agent

---

## Overview

This project is a self-hosted cloud lab built on a 3-node Raspberry Pi cluster, designed to simulate real-world infrastructure while running a custom AI-powered lead generation and outreach system.

**Core components:**

- Kubernetes (k3s)
- NFS persistent storage
- Prometheus + Grafana monitoring
- FastAPI-based AI lead analysis application

---

## Architecture

Home Network (Router)
        |
      Switch
  -------------------------
  |           |           |
pi-control  pi-worker  pi-storage
(Control)    (Apps)      (NFS)

        Kubernetes Cluster
               |
        AI Lead Agent
               |
     Prometheus + Grafana

---

## Hardware

- 3 × Raspberry Pi 4
- Micro server rack
- 6-port 60W power supply
- Network switch
- 512GB USB flash drive (storage node)
- MicroSD cards
- Ethernet cabling

---

## Platform Stack

### Kubernetes (k3s)
- Lightweight Kubernetes for ARM
- Control plane + worker node architecture
- Containerized workloads

### Persistent Storage
- USB storage mounted on pi-storage
- Shared via NFS
- Kubernetes PersistentVolume + PersistentVolumeClaim

### Monitoring
- Prometheus (metrics collection)
- Node Exporter (node-level metrics)
- Grafana (dashboards)

---

## AI Lead Agent

A FastAPI-based application that analyzes business websites and generates outreach opportunities.

### Lead Input
- Single submission
- Bulk input
- CSV upload

### Website Analysis
- HTTPS detection
- SEO validation
- Mobile responsiveness
- Load performance
- Content depth
- CTA detection
- Contact info detection

### Lead Scoring
- High opportunity
- Medium opportunity
- Low opportunity

### Outreach Generation
- Personalized message
- Subject line
- Email-ready draft

---

## Lead Workflow

### Status Lifecycle

new → reviewed → ready_to_contact → contacted → replied → closed  
                                     ↘ not_interested

### Outreach Queue

Displays only actionable leads:

- ready_to_contact
- contacted
- replied

Includes:
- Subject line
- Outreach message
- Email draft

---

## Data Storage

- Leads stored as JSON
- Persisted via NFS
- Survives pod restarts

---

## Deployment

- FastAPI app containerized with Docker
- Deployed to Kubernetes
- Uses PersistentVolumeClaim
- Exposed via NodePort

---

## Challenges Solved

### Infrastructure
- Kubernetes on ARM (Raspberry Pi)
- NFS + Kubernetes integration
- Persistent storage issues

### Networking
- Hostname resolution
- NFS mounting
- Pod communication

### Application
- CrashLoopBackOff debugging
- Template issues
- File extension conflicts

---

## Skills Demonstrated

- Linux administration
- Kubernetes (k3s)
- Docker
- NFS storage design
- Monitoring (Prometheus + Grafana)
- FastAPI development
- Debugging distributed systems
- Workflow automation

---

## Project Milestones

- [x] Built Raspberry Pi cluster
- [x] Installed k3s
- [x] Configured NFS storage
- [x] Deployed workloads
- [x] Implemented monitoring
- [x] Built FastAPI app
- [x] Added lead analysis
- [x] Implemented bulk + CSV input
- [x] Built scoring system
- [x] Created outreach generator
- [x] Added status tracking
- [x] Built outreach queue
- [x] Added email-ready workflow

---

## Current State

Fully operational system with:

- Kubernetes cluster
- Persistent storage
- Monitoring stack
- Lead analysis + outreach pipeline

---

## Future Enhancements

- Lead detail page (mini CRM)
- Authentication
- Email API integration
- Automated lead discovery
- Follow-up automation
- Analytics dashboard

