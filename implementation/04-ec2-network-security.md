# Phase 4 — Compute + Network Security

## Launch EC2 Instance
Steps:
1. EC2 → Launch Instance
2. Amazon Linux 2023
3. Instance type: t3.micro
4. Default VPC
5. Create key pair
6. Configure Security Group:
   - SSH (port 22)
   - Source: My IP only (/32)
   - Do NOT use 0.0.0.0/0

## SSH Test
Command:
```bash
ssh -i key.pem ec2-user@public-ip



Validation:

SSH connection successful from approved IP

Security Group Verification

Test:

Turn on VPN (public IP changes)

SSH connection fails as expected

Result:

Security Group correctly enforced IP restriction
