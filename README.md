# Secure Cloud Foundation Deployment (Production-Minded Mini Architecture)

## Summary
This project implements a secure, access-controlled, and cost-governed AWS cloud environment simulating a small company workload. The focus is secure configuration (not feature complexity).

## Objectives
1. Establish secure AWS account baseline configuration
2. Implement identity and access control using IAM
3. Deploy compute resource with restricted network exposure
4. Protect storage using secure configuration and encryption
5. Implement cost monitoring to prevent financial risk
6. Demonstrate AWS Shared Responsibility Model understanding

## Deliverables
- 📄 Final report with step-by-step implementation + validation + screenshots: **[final-report.pdf](final-report.pdf)**
- Architecture summary: **[architecture.md](architecture.md)**
- Evidence index: **[evidence/README.md](evidence/README.md)**

## Core Components
- Hardened AWS Account (Root MFA)
- IAM (Admin + ReadOnly model)
- Default VPC
- Security Group (SSH restricted to My IP /32)
- EC2 (Amazon Linux 2023, t3.micro)
- S3 (Block Public Access + SSE-S3)
- AWS Budget ($5 monthly, 80% alert)

## Status
Project Completed Successfully.
