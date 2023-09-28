## Using Variables in Terraform

### Interactive Mode

#### Define Terraform

```terraform
# variables.tf

variable "filename" {
}
variable "content" {
}
variable "prefix" {
}
variable "separator" {
}
variable "length" {
}
```

```terraform
# main.tf

resource local_file pet {
  filename = var.filename
  content  = var.content
}

resource random_pet my-pet {
  prefix    = var.prefix
  separator = var.separator
  length    = var.length
}
```

#### Terraform Apply

```shell
terraform apply
```

```shell
var.content
  Enter a value: We love pets!

var.filename
  Enter a value: /root/pets.txt
 
var.length
  Enter a value: 2
 
var.prefix
  Enter a value: Mrs
 
var.separator
  Enter a value: .
```

### Command Line Flags

```shell
terraform apply -var "filename=/root/pets.txt" -var "content=We love Pets!" -var "prefix=Mr" -var "separator=." -var "length=2"
```

### Environment Variables

```shell
export TF_VAR_filename="/root/pets.txt"
export TF_VAR_content="We love pets!"
export TF_VAR_prefix="Mrs"
export TF_VAR_separator="."
export TF_VAR_length=2
terraform apply
```

### Variable Definition Files

```terraform
# terraform.tfvars

filename  = "/root/pets.txt"
content   = "We love pets!"
prefix    = "Mrs"
separator = "."
length    = 2
```

```shell
terraform apply
```

#### Automatically Loaded Pattern

- `terraform.tfvars`
- `terraform.tfvars.json`
- `*.auto.tfvars`
- `*.auto.tfvars.json`

#### Apply Specific File

```shell
terraform apply -var-file variables.tfvars
```

### Variable Definition Precedence

```terraform
# main.tf

resource local_file pet {
  filename = var.filename
}
```

```terraform
# variables.tf

variable filename {
  type = string
}
```

```shell
export TF_VAR_filename="/root/cats.txt"
```

```terraform
# terraform.tfvars

filename = "/root/pets.txt"
```

```terraform
# variables.auto.tfvars

filename = "/root/my-pets.txt"
```

```shell
terraform apply -var "filename=/root/best-pets.txt"
```

| Order | Option                                | Applied |
|:-----:|---------------------------------------|:-------:|
|   1   | Environment Variables                 |    X    |
|   2   | terraform.tfvars                      |    X    |
|   3   | *.auto.tfvars(alphabetical order)     |    X    |
|   4   | -var or -var-file(command-line flags) |    O    |
