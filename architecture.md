# Architecture Overview

## Core Components
- AWS Account (Hardened)
- IAM (Identity & Access Management)
- Default VPC
- Security Group (Restricted SSH)
- EC2 Instance (Compute Layer)
- S3 Bucket (Private Storage)
- AWS Budget (Cost Monitoring)

## How the Architecture Works
1. The AWS Account provides the cloud control plane.
2. IAM controls who can access resources and what actions they can perform.
3. The Default VPC provides isolated networking.
4. EC2 instance runs inside the VPC.
5. Security Group acts as a stateful firewall controlling inbound traffic.
6. S3 bucket stores company data securely with public access blocked.
7. AWS Budget monitors spending and triggers alerts.

## Data Flow
User → IAM Authentication → EC2 via Security Group → S3 (private storage)

## Main Security Controls
- Root MFA enabled
- No daily root usage
- Least privilege IAM model
- SSH restricted to specific IP (/32)
- S3 Block Public Access enabled
- Default encryption for S3 (SSE-S3)
- Budget alert to prevent financial abuse
