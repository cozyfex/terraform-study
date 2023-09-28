## Install Terraform

### MacOS

```shell
brew tap hashicorp/tap
brew install hashicorp/tap/terraform
```

### Check Version

```shell
terraform versoin
```

### HashiCorp Configuration Language(HCL)

```hcl
resource "aws_instance" "web-server" {
  ami           = "ami-00000000"
  instance_type = "t2.micro"
}
```

