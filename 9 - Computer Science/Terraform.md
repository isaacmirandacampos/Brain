**Created:** 2023-12-11
**Tags:** #aws #productivity #cloudservices

## What is Terraform?
Terraform is a infrastructure as code tool developed by HashiCorp. It allow that users manager the cloud infrastructure using declarative language.
We can make a plan before apply the changes and the terraform has **idempotence**, run the same code don't change existent infrastructure.
Allow support multiple cloud service, that as: *aws, azure and gcp*.
We can manager our infrastructure at the repository level, spliting in multiple enviroments *(QA,production)*. It maked using workspaces.
