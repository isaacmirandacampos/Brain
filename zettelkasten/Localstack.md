created:: 2024-04-14 09:32
status:: #zettel/permanent 
tags:: #cloud #aws
## What is Localstack?
Localstack is a cloud service emulator that run local without connection with a remote cloud service.
### Why use it?
A benefit that use localstack is run test locally without deploy a code, it is more productivity because we can know how we code run in cloud without deploys, it is a easily for we deadline tasks.
**We can use it to learn a new resource without worry about price**
### Ways to use it
The best way to use localstack is creating a docker-compose. It enable you use the best of localstack without install dependencies. If you want, you can install awslocal cli to check the services running in localstack docker. But the most good is use the online service of localstack, that enable you check the state of services and operate on there.
A way of how orchestration of localstack is using [[Terraform]], you only need create a code and set up the urls of services defined in terraform to use the localstack.

