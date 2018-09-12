# Terraform Azure MSI Example

This will use Terraform to deploy a VM Scale Set with Managed Service Identity on Azure.

Requirements:
```
azure-cli
terraform
```

Login to Azure with your Azure CLI.
``` 
$ az login
```

Choose the correct subscription to deploy to.
```
$ az account list -o table
```
```
$ az account set -s <SUBSCRIPTION_ID>
```

Initialize Terraform.
```
$ terraform init
```

Plan the project.
```
$ terraform plan -out plan.out
```

Deploy the Virtual Machine Scale Set on Azure.
```
$ terraform apply "plan.out"
```

You can now ssh into your VMs using the NAT Rules
```
Apply complete! Resources: 0 added, 0 changed, 0 destroyed.

Outputs:

scaleset_publicip = xxx.xxx.xxx.xxx
```
For example, if instance is in NAT pool 50000:
```
$ ssh azureuser@xxx.xxx.xxx.xxx -p 50000
```
