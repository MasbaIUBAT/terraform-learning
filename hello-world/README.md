# Lab 01: Hello World

## Objective

Learn output blocks, plan, apply, and local state without creating cloud infrastructure. No provider or cloud credentials are required.

## Configuration

[main.tf](main.tf):

```hcl
output "hello_one" {
  value = "Hello World"
}
```

`output` is the block type, `hello_one` is its name, and `value` specifies the result. Braces contain the block body. The original exercise used `first.tf`; this repository uses `main.tf`. Both filenames work. Do not duplicate the output in both files: Terraform reads all `.tf` files in the folder together.

## Run the lab

Open a terminal in this `hello-world` folder. These commands work in CMD, PowerShell, or Linux.

```sh
terraform -version
terraform init
terraform fmt -check
terraform validate
terraform plan
terraform apply
terraform output
```

| Command | Purpose |
| --- | --- |
| `terraform -version` | Check installation |
| `terraform init` | Initialize the working directory |
| `terraform fmt -check` | Check formatting; use `terraform fmt` to fix it |
| `terraform validate` | Check configuration validity |
| `terraform plan` | Preview proposed changes |
| `terraform apply` | Apply after reviewing and entering `yes` |
| `terraform output` | Read saved output values |

This simple output-only example also works directly with plan/apply, as in the original exercise. Initialization is included to establish the normal workflow for future provider-based labs.

## Expected results

Plan includes:

```text
Changes to Outputs:
  + hello_one = "Hello World"
```

The plus sign means an output will be added. The note about not using `-out` is informational: no separate plan file was saved. A normal apply generates a fresh plan.

Apply includes:

```text
Apply complete! Resources: 0 added, 0 changed, 0 destroyed.

Outputs:

hello_one = "Hello World"
```

## Where is the result saved?

With the default local backend, apply writes `terraform.tfstate` inside this lab folder. It stores the output and an empty resources list. Nothing is created in AWS or another cloud.

| File | Purpose |
| --- | --- |
| `main.tf` | Instructions written by you |
| `terraform.tfstate` | Terraform-managed output and resource records |

Edit configuration rather than state. State is excluded from Git because real projects can contain sensitive values in it.

## Try an update

Change the value to `"Hello Terraform"`, save, then run plan, apply, and output again. A subsequent plan without changes should report no changes. Restore `"Hello World"` and apply to return to the initial exercise.

## Windows troubleshooting

Use `cd` to enter a folder; typing a directory path alone does not navigate. In CMD, the original practice folder was opened with:

```cmd
cd /d C:\Users\HP\terraform-practice
code .
```

For this repository, enter its `hello-world` subfolder instead. If `code` is not recognized, reopen the terminal or use VS Code → File → Open Folder.

```cmd
where.exe terraform
dir
```

These locate the executable and list files. If Terraform is not recognized, add its executable folder to PATH and reopen terminals and VS Code. Save edits with Ctrl+S before planning.

## Validation record

The original equivalent Hello World configuration was successfully planned and applied on Windows with Terraform v1.17.1 (`windows_386`), and its local state was inspected. The additional init, formatting, and validation commands documented here were not independently executed in this environment.
