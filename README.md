Raspberry Pi Cloud Lab + AI Lead Agent
Overview

This project documents the design and implementation of a 3-node Raspberry Pi homelab used to simulate a real-world cloud infrastructure environment and host a custom-built AI-powered lead generation and outreach system.

The lab combines:

Kubernetes (k3s) cluster deployment

NFS-backed persistent storage

Monitoring with Prometheus and Grafana

A custom FastAPI-based application for business lead analysis and outreach generation

The goal of this project is to demonstrate hands-on cloud engineering, DevOps, and AI integration skills in a fully self-hosted environment.

Architecture
Infrastructure Layer

3-node Raspberry Pi cluster:

pi-control → Kubernetes control plane

pi-worker → application workloads

pi-storage → NFS storage + monitoring target

Local network with unmanaged switch

USB-backed storage mounted and shared via NFS

Platform Layer

Kubernetes (k3s)

Persistent Storage (NFS)

Monitoring Stack

Prometheus

Node Exporter

Grafana

Application Layer

AI Lead Agent (FastAPI)

Website analysis engine

Lead scoring system

Outreach generation

Workflow tracking system

System Diagram
                    Home Router
                         |
                       Switch
          -----------------------------------
          |                |                |
     pi-control       pi-worker        pi-storage
   Kubernetes CP     App Workloads     NFS Storage
          |                |                |
          |--------- Prometheus ----------->|
          |                |
          |------------- Grafana -----------|
          |
          |------ AI Lead Agent (FastAPI) ------|
Hardware

3 × Raspberry Pi 4

Micro server rack

6-port 60W power supply

Network switch

512GB USB flash drive (storage node)

MicroSD cards

Ethernet cables

Core Features
Kubernetes Cluster

k3s deployed on Raspberry Pi

Control plane + worker node configuration

Workload scheduling and service exposure

Persistent Storage

USB storage mounted on pi-storage

Shared via NFS

Kubernetes PersistentVolume + PersistentVolumeClaim

Used for application data and lead storage

Monitoring & Observability

Prometheus for metrics collection

Node Exporter on each node

Grafana dashboards for:

CPU usage

memory usage

disk utilization

pod health

Alert rules for:

node failure

high CPU usage

high memory usage

AI Lead Agent Application

A custom-built web application designed to identify business opportunities and assist with outreach.

Capabilities
Lead Input

Single lead submission

Bulk input (multi-line paste)

CSV upload for batch processing

Website Analysis

HTTPS detection

SEO checks (title, meta description)

Mobile optimization detection

load time measurement

content depth analysis

navigation and CTA detection

contact info detection

Lead Scoring

Opportunity-based scoring model (higher score = higher opportunity)

Priority classification:

High

Medium

Low

Offer Generation

Suggested service offering based on detected issues

Estimated price range

Outreach Generation

Personalized outreach message

Email subject line generation

Lead Management Workflow
Status Tracking

Each lead is stored with a lifecycle status:

new

reviewed

ready_to_contact

contacted

replied

closed

not_interested

Outreach Queue

Filtered view showing only:

ready_to_contact

contacted

replied

Includes:

outreach message

subject line

one-click email draft (mailto link)

Data Storage

Leads saved as JSON files

Stored on NFS-backed storage

Persistent across pod restarts

Example:

{
  "status": "ready_to_contact",
  "subject": "Quick idea for improving Joe's Plumbing website",
  "analysis": { ... },
  "outreach": "..."
}
Application Deployment

FastAPI app containerized with Docker

Deployed to Kubernetes

Uses PersistentVolumeClaim for data storage

NodePort service for access

Key Challenges Solved
Infrastructure

Kubernetes setup on ARM (Raspberry Pi)

NFS integration with Kubernetes

Persistent storage binding issues

Networking

hostname resolution issues

NFS mount failures

pod scheduling + image distribution

Application

template mismatch debugging

container crash troubleshooting

file extension issues from Windows (.txt)

Kubernetes Debugging

CrashLoopBackOff resolution

ErrImagePull / local image handling

permission issues with kubeconfig

Skills Demonstrated

Linux system administration

Kubernetes (k3s) deployment and troubleshooting

containerization with Docker

persistent storage (NFS) design

cloud architecture principles

infrastructure monitoring (Prometheus/Grafana)

FastAPI application development

debugging distributed systems

workflow automation design

basic AI-assisted logic integration

Project Milestones

Built Raspberry Pi cluster

Installed and configured k3s

Configured NFS persistent storage

Deployed test workloads

Implemented monitoring stack

Built and deployed custom FastAPI app

Implemented website analysis engine

Added bulk and CSV lead ingestion

Implemented lead scoring system

Built outreach generation engine

Added status tracking workflow

Built outreach queue system

Added email-ready workflow

Current Status

The platform is fully operational and supports:

multi-node Kubernetes cluster

persistent application storage

real-time monitoring

scalable lead analysis workflows

structured outreach pipeline

Future Enhancements

lead detail page with notes and follow-up tracking

contact information management

authentication and access control

automated lead discovery (Google Maps / directories)

email API integration (Gmail/SendGrid)

follow-up automation workflows

dashboard for pipeline metrics

AI-enhanced analysis and recommendations
