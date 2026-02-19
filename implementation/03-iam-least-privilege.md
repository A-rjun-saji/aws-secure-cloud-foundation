# Phase 3 — IAM Least Privilege Model

## Create ReadOnly Group
Steps:
1. IAM → User Groups → Create group
2. Name: ReadOnlyGroup
3. Attach policy: ReadOnlyAccess

## Create ReadOnly User
Steps:
1. IAM → Users → Create user
2. Add to ReadOnlyGroup
3. Enable console login
4. Test login

Validation:
- ReadOnly user cannot launch EC2
- Can only view resources
