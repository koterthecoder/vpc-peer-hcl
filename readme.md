# Sample VPC Peering using Terraform


### Requirements
- Two AWS profiles
    - Ex: infra - infrastructure account
    - EX: sec   - security account

### login to infrastructure account
```aws configure --profile infra```

### login to security account
```aws configure --profile infra```


### initialize the tf configuration
```terraform init```

### plan the tf deployment
```terraform plan -out roles.tfplan```

### apply the deployment
```terraform apply "roles.tfplan"```