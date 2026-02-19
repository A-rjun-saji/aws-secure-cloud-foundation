# Phase 1 — Account Hardening (Non-Negotiable)

## Enable Root MFA
Steps:
1. Login as root
2. IAM → Security credentials
3. Enable MFA on root
4. Use authenticator app
5. Verify login with MFA

Validation:
- Root shows “MFA Enabled”

## Create IAM Admin User (Daily Use Account)
Steps:
1. IAM → Users → Create user
2. Username: admin-user
3. Enable console access
4. Attach policy: AdministratorAccess
5. Download credentials
6. Logout root and login as admin-user

Validation:
- Admin can access services
- Root not used again
