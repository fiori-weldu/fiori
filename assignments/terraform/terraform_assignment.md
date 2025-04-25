# Terraform Templates

## General

### Questions

| Can Answer? | # | Question |
| --- | --- | --- |
| <input type="checkbox"> | 1 | What Terraform templates are used for? |
| <input type="checkbox"> | 2 | What file format Terraform templates use? |
| <input type="checkbox"> | 3 | What are the major differences between ARM and Terraform templates? |
| <input type="checkbox"> | 4 | What is Terraform state file used for? |
| <input type="checkbox"> | 5 | How can Terraform get authenticated to talk to Azure Resource Manager? |

### Assignments

| Done? | # | Assignment |
| --- | --- | --- |
| <input type="checkbox"> | 1 | Write a Terraform configuration file (template) for a VM deployment (with custom RG, VNet, subnet, NSG, NIC, PIP). Run terraform init, validate, plan, and apply commands to deploy the VM (save the screenshots). |
| <input type="checkbox"> | 2 | Use variables in your configuration file. Pass the variable values through the defaults, command line arguments (save the screenshot), and variable values files. |
| <input type="checkbox"> | 3 | Use locals and built-in functions in your configuration file. |
| <input type="checkbox"> | 4 | Use outputs in your configuration file. |
| <input type="checkbox"> | 5 | Use both implicit and explicit dependencies in your configuration file. |
| <input type="checkbox"> | 6 | Use a data source in your configuration file. |
| <input type="checkbox"> | 7 | Add existing Azure resource to your configuration and state file without redeploying it in Azure. Use import command and (Bonus) import block. Remove existing Azure resource from your configuration file and the state file without decommissioning it from Azure (save the screenshots). |
| <input type="checkbox"> | 8 | Use count and for-each property in your configuration file to deploy multiple storage accounts or similar simple resources. (Bonus) Use a "dynamic" block to  configure multiple similar resource properties at once. |
| <input type="checkbox"> | 9 | Use the count property to achieve conditional deployment in your configuration file. |
| <input type="checkbox"> | 10 | Use a module in your configuration file. |
| <input type="checkbox"> | 11 | Configure the use of the remote state file in your configuration file. |
| <input type="checkbox"> | 12 | (Bonus) Configure the use of a service principle to authorize the deployment of resources to Azure. Pass the service principle credentials via environmental variables. |
