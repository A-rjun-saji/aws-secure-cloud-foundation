# Secure Cloud Foundation Deployment (Production-Minded Mini Architecture)

## Introduction
This project implements a secure, access-controlled, and cost-governed AWS cloud environment that simulates a small company workload. The focus is secure configuration (not feature complexity).

## Objectives
1. Establish secure AWS account baseline configuration
2. Implement identity and access control using IAM
3. Deploy compute with restricted network exposure
4. Protect storage using secure configuration and encryption
5. Implement cost monitoring to prevent financial risk
6. Demonstrate AWS Shared Responsibility Model understanding

## Architecture
See: [architecture.md](architecture.md)

Core components:
- AWS Account (Hardened)
- IAM (Admin + ReadOnly model)
- Default VPC
- Security Group (SSH restricted to My IP /32)
- EC2 (Amazon Linux 2023, t3.micro)
- S3 (Block Public Access + SSE-S3)
- AWS Budget ($5 monthly, 80% alert)

## Implementation
Steps are documented in the [implementation](implementation/) folder.

## Evidence
Screenshots and proof: [evidence](evidence/)

## Status
Project Completed Successfully.
