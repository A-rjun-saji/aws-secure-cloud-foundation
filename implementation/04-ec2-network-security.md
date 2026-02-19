# Phase 4 — Compute + Network Security

## Objective
Deploy a hardened EC2 instance with restricted SSH access using Security Groups.

---

## Launch EC2 Instance

### Configuration Steps

1. Navigate to **EC2 → Launch Instance**
2. Select **Amazon Linux 2023**
3. Choose instance type: `t3.micro`
4. Select **Default VPC**
5. Create and download a **key pair (.pem)** — store securely
6. Configure **Security Group (Inbound Rules)**:
   - Type: SSH
   - Protocol: TCP
   - Port: 22
   - Source: **My IP (/32)**
   - Do NOT allow: `0.0.0.0/0`

---

## Validation

- SSH connection succeeds **only from your approved public IP**
- Security Group inbound rule shows:
TCP 22 → Your_Public_IP/32


---

## Security Test (Access Control Verification)

1. Connect from your normal network → SSH should succeed
2. Enable VPN (public IP changes)
3. Attempt SSH again → Connection should fail

### Expected Result

Security Group correctly enforces IP-based SSH restriction.

---

## SSH Command

```bash
ssh -i key.pem ec2-user@<public-ip>
