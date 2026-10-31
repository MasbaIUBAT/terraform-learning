# Terraform Learning

Hands-on Terraform practice by **Masba Uddin Rumi**, with code, commands, expected results, and explanations.

## Labs

| Lab | Topics | Cloud account |
| --- | --- | --- |
| [Hello World](hello-world/README.md) | Outputs, plan, apply, local state | Not required |

## Quick start

Install [Terraform](https://developer.hashicorp.com/terraform/install) and Git. For Intel/AMD 64-bit Windows, choose Windows AMD64. VS Code with the HashiCorp Terraform extension is optional.

```sh
git clone https://github.com/MasbaIUBAT/terraform-learning.git
cd terraform-learning/hello-world
terraform init
terraform validate
terraform plan
terraform apply
terraform output
```

Review the plan and enter `yes` when prompted. This lab creates no cloud resources and incurs no cloud charges.

## Future practice

Create a separate folder for each exercise with its configuration and README, then add a link above. Run Terraform inside each lab folder to keep local state separate.

## Version control

Commit configuration, documentation, and `.terraform.lock.hcl` when generated. Exclude state, downloaded providers, saved plans, credentials, and private keys. Review staged changes; `.gitignore` does not remove files already tracked.
