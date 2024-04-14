created:: 2024-04-14 09:07
status:: #zettel/permanent 
tags:: #cloud #iac

## What is Terraform?
Terraform is a infrastructure as code tool developed by HashiCorp. It allow that users manager the cloud infrastructure using declarative language.
We can make a plan before apply the changes and the terraform has **idempotence**, run the same code don't change existent infrastructure.
Allow support multiple cloud service, that as: *aws, azure and gcp*.
We can manager our infrastructure at the repository level, spliting in multiple enviroments *(QA,production)*. It maked using workspaces.
## Remote state
A possible way to store the state of your terraform changes in a s3 bucket. With this, can avoid expose sensitive keys when upload your code to a git manager.
## Modules
Can create modules to reuse in the code, the modules can have a initial value and you only can override this properties. The modules do not need be created in the `terraform init` context to be reused.

# References
- [10 Boas Praticas para projetos de Terraform | Unicast Cloud](https://unicast.com.br/posts/10-boas-praticas-para-projetos-terraform/)
- [Backend Configuration - Configuration Language | Terraform | HashiCorp Developer](https://developer.hashicorp.com/terraform/language/settings/backends/configuration)