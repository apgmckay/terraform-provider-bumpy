# Bumpy Terraform Provider

This repo contains code for the [Bumpy](https://github.com/apgmckay/bumpy) terraform provider.

Setup a `$HOME/.terraformrc` file something like the below:

```
provider_installation {
  dev_overrides {
    "registry.terraform.io/bumpycorp/bumpy" = "/absolute/path/to/bumpy/terraform_provider"
  }
  direct {}
}
```

This allows for overriding of the registry config for local development, which means that you don't need to install terraform providers via `terraform init`.

Compile the terraform provider using the [task](https://taskfile.dev) file.

Start the grpc server for the compiled provder, this will return you a `TF_REATTACH_PROVIDERS` environment variable that you will need to set in the shell where you are going to run terraform, in this doc we will use the example/ dir.

Change directories in to example and run terraform.

```
# Set TF_REATTACH_PROVIDERS returned from setting up the grpc server for the terraform provider 
cd example
terraform plan
terraform apply
```
