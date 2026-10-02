# Enterprise Secure Hub-and-Spoke Migration & Operations Platform

## Project Overview

This project designs and implements an enterprise-style Microsoft Azure platform for a fictional organisation, Contoso Services, transitioning workloads from a traditional Windows Server and VMware environment to Azure.

The platform will support both modern PaaS workloads and legacy IaaS workloads while implementing enterprise networking, security, identity, Infrastructure as Code, CI/CD, observability, backup, disaster recovery, and operational controls.

The environment is implemented in a personal Azure subscription with cost-conscious resource sizing and lifecycle management.

## Business Scenario

Contoso Services currently operates traditional Windows Server and VMware infrastructure and is establishing an Azure landing platform for both modern and legacy applications.

The organisation requires a platform that:

- Separates shared connectivity/security services from application workloads.
- Supports both PaaS and IaaS workloads.
- Protects Internet-facing applications from common web attacks.
- Prevents databases and supporting PaaS services from being directly exposed to the Internet.
- Provides controlled and centralised outbound Internet connectivity.
- Supports future workload expansion without redesigning the core network.
- Uses Infrastructure as Code for repeatable deployments.
- Introduces source control, validation, approval, and controlled deployment workflows.
- Implements least-privilege access.
- Provides monitoring, alerting, backup, and disaster recovery capabilities.

## Workloads

### Modern Application

A PaaS-first customer-facing application using:

- Azure Application Gateway with Web Application Firewall
- Azure App Service
- Azure SQL Database
- Managed Identity
- Azure Key Vault
- Private Endpoints and Private DNS

### Legacy Application

A Windows-based application retained on IaaS during the initial migration stage using:

- Azure Application Gateway
- Internal Load Balancer
- Windows Virtual Machines / Virtual Machine Scale Sets
- Network Security Groups

## Architecture Strategy

The platform uses a hub-and-spoke network topology.

The hub provides centralised shared connectivity and security services.

Two workload spokes provide isolation between:

1. PaaS application workloads
2. IaaS compute workloads

Centralised outbound Internet traffic will be evaluated and implemented using Azure Firewall and User Defined Routes.

Detailed architecture decisions and trade-offs will be documented using Architecture Decision Records (ADRs).

## Engineering Approach

Infrastructure will be implemented progressively using Terraform.

The project will evolve through:

1. Architecture and requirements
2. Governance and identity
3. Infrastructure as Code
4. Networking and security
5. Application platform services
6. Managed identity and secrets management
7. CI/CD
8. Monitoring and observability
9. Backup and disaster recovery
10. Operational automation
11. Controlled failure and troubleshooting exercises

Changes will be developed using feature branches and integrated through pull requests rather than developed directly on the main branch.

## Project Status

**Current stage:** Foundation and repository setup.