# Sample VPC Peering using Terraform

**Goal:** Create configuration to allow VPC peering between a two accounts (ex security and infrastructure)

## Application

This repo can be applied to either infrastructure repo: `vpc-hcl` or `multi-vpc-hcl`

The nested directory `security` which contains configuration for the security vpc


## Requirements
- Two AWS profiles
    - Ex: infra - infrastructure account
    - EX: sec   - security account
- Acceptor: Security account
    - peering-policy
    - peering-role
- Requestor: Infrastructure account
    - peering-group
    - assume-role-policy

## Instruction Order

1. Run `vpc-hcl/main.tf` to deploy requestor VPC
1. Run `vpc-peer-hcl/security/main.tf` to deploy acceptor VPC
1. Run `vpc-peer-hcl/main.tf` to deploy peering policy, role, group, etc
1. Run `vpc-hcl/peering.tf` to deploy connection resources

## To run this repo

### login to infrastructure account
```aws configure --profile infra```

### login to security account
```aws configure --profile sec```

### initialize the tf configuration
```terraform init```

### plan the tf deployment
```terraform plan -out roles.tfplan```

### apply the deployment
```terraform apply "roles.tfplan"```