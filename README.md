Secure Cloud Foundation Deployment (Production-Minded Mini Architecture)
________________________________________
 Introduction
This project implements a secure, access-controlled, and cost-governed AWS cloud environment that simulates a small company workload.
The objective is to demonstrate foundational cloud architecture, security controls, and financial governance aligned with AWS best practices.
The deployment focuses on secure configuration rather than feature complexity.
________________________________________
Project Objective
The main objectives of this project are:
1.	Establish secure AWS account baseline configuration
2.	Implement identity and access control using IAM
3.	Deploy compute resource with restricted network exposure
4.	Protect storage using secure configuration and encryption
5.	Implement cost monitoring to prevent financial risk
6.	Demonstrate understanding of AWS Shared Responsibility Model
________________________________________
Scope of the Project
Included:
•	AWS account hardening
•	IAM user and group implementation
•	EC2 deployment with restricted Security Group
•	S3 bucket with Block Public Access enabled
•	AWS Budget configuration
Not Included:
•	Multi-tier architecture
•	Load balancers
•	Auto scaling
•	Infrastructure as Code
•	Advanced networking
This project focuses strictly on foundational security architecture.
________________________________________
5. Architecture Overview
Core Components:
•	AWS Account (Hardened)
•	IAM (Identity & Access Management)
•	Default VPC
•	Security Group (Restricted SSH)
•	EC2 Instance (Compute Layer)
•	S3 Bucket (Private Storage)
•	AWS Budget (Cost Monitoring)
________________________________________
 How the Architecture Works
1.	The AWS Account provides the cloud control plane.
2.	IAM controls who can access resources and what actions they can perform.
3.	The Default VPC provides isolated networking.
4.	EC2 instance runs inside the VPC.
5.	Security Group acts as a stateful firewall controlling inbound traffic.
6.	S3 bucket stores company data securely with public access blocked.
7.	AWS Budget monitors spending and triggers alerts.
Data flow:
User → IAM Authentication → EC2 via Security Group → S3 (private storage)
________________________________________
Main Security Controls Implemented
•	Root MFA enabled
•	No daily root usage
•	Least privilege IAM model
•	SSH restricted to specific IP
•	S3 Block Public Access enabled
•	Default encryption for S3
•	Budget alert to prevent financial abuse
________________________________________
Shared Responsibility Context
AWS Responsible For:
•	Physical data centers
•	Hardware
•	Network infrastructure
•	Hypervisor
Customer Responsible For:
•	IAM configuration
•	Security Group rules
•	Data encryption
•	OS-level security inside EC2
•	Cost control
This project validates understanding of “security in the cloud.”
________________________________________
Risk Mitigation Strategy
Risk	Control Implemented
Account takeover	Root MFA
Over-privileged access	IAM least privilege
SSH brute force	Restricted IP
Data leakage	S3 Block Public Access
Unexpected cost spike	AWS Budget
________________________________________
Expected Learning Outcomes
After completion, the implementer will be able to:
•	Explain Shared Responsibility Model
•	Implement IAM securely
•	Configure network access controls
•	Secure S3 storage
•	Understand AWS pricing behavior
•	Navigate AWS Console confidently
________________________________________
 Success Criteria
Project is successful if:
•	No resource is publicly exposed
•	IAM follows least privilege
•	Budget alert is functional
•	EC2 accessible only from approved IP
•	S3 objects are not publicly readable




 Implementation Procedure (Step-by-Step Execution)
________________________________________
Phase 1 — Account Hardening (Non-Negotiable)
 Enable Root MFA
1.	Login as root
2.	Go to: IAM → Dashboard> security credentials
3.	Enable MFA on root account
 
4.	Use authenticator app
5.	Verify login with MFA
Validation:
•	Root shows “MFA Enabled”

 
________________________________________
Create IAM Admin User (Daily Use Account)
1.	IAM → Users → Create user
2.	Username: admin-user
 

3.	Enable console access
4.	Attach policy: AdministratorAccess
 

5.	Download credentials
Logout root.
Login using admin-user.
Validation:
•	Admin can access services
•	Root not used again

 
________________________________________
Phase 2 — Cost Governance Setup
 Create AWS Budget
1.	Billing → Budgets → Create Budget
2.	Type: Cost Budget
 
3.	Monthly
4.	Amount: $5
5.	Add email alert at 80%
 

 
Validation:
•	Budget visible in dashboard
•	Email alert configured
 

________________________________________
Phase 3 — IAM Least Privilege Model
 Create ReadOnly Group
1.	IAM → User Groups → Create group
2.	Name: ReadOnlyGroup
 
3.	Attach policy: ReadOnlyAccess
 
________________________________________
 Create ReadOnly User
1.	IAM → Users → Create user

 
2.	Add to ReadOnlyGroup
3.	Enable console login

 
4.	Test login
Validation:
•	ReadOnly user cannot launch EC2
•	Can only view resources
 

________________________________________
Phase 4 — Compute + Network Security
Launch EC2 Instance
1.	EC2 → Launch Instance
2.	Choose Amazon Linux 2023
3.	Instance type: t3.micro (Free tier)
 

 
4.	Use default VPC
5.	Create key pair
6.	Configure Security Group:
o	SSH (port 22)
o	Source: My IP only
DO NOT use 0.0.0.0/0.
 

Launch instance.
 
________________________________________
 SSH Test
From terminal:
ssh -i key.pem ec2-user@public-ip
Confirm connection works.


 
________________________________________
 Security Group Verification
•	Try connecting from another IP (optional test)
•	Confirm connection fails  : I turn on the vpn therefore the IP has changed 
 
________________________________________
Phase 5 — Storage Hardening
 Create Secure S3 Bucket
1.	S3 → Create bucket
2.	Unique name
3.	Keep Block Public Access = ON
4.	Enable default encryption (SSE-S3)
Create bucket.

 
________________________________________
 Upload Test Object
Upload a small text file/img.
 

Try accessing via public URL.
Expected: Access Denied.
 
________________________________________
Phase 6 — Architecture Validation
 Verify Security Controls
Check:
•	Root MFA enabled
•	No public SSH
•	ReadOnly user restricted
•	S3 not public
•	Budget active
________________________________________
Phase 7 — Cleanup (Cost Control Discipline)
 Terminate EC2
1.	EC2 → Instance → Terminate
2.	Delete unused EBS volumes
3.	Keep S3 bucket only if needed
Failure to cleanup = cost leak.
Final Statement
This Secure Cloud Foundation Deployment demonstrates practical implementation of core AWS security principles, identity management, network restriction, storage protection, and cost governance.
It establishes a validated baseline required before advancing to higher-level AWS architecture or cloud security engineering topics.
Project Completed Successfully.

