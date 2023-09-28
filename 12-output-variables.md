## Output Variables

### Syntax

```
output <variable_name> {
    value = <variable_value>
    <arguments>
}
```

### Usage

- Output to `Ansible`
- Output to `Shell Script`

### Example

```terraform
# variables.tf

variable "filename" {
  default = "/root/pets.txt"
}
variable "content" {
  default = "We love pets!"
}
variable "prefix" {
  default = "Mrs"
}
variable "separator" {
  default = "."
}
variable "length" {
  default = 1
}
```

```terraform
# main.tf

resource local_file pet {
  filename = var.filename
  content  = "My favorite pet is ${random_pet.my-pet.id}"
}

resource random_pet my-pet {
  prefix    = var.prefix
  separator = var.separator
  length    = var.length
}
```

```terraform
# output.tf

output pet-name {
  value = random_pet.my-pet.id
}
```

```shell
terraform apply
```

```shell
terraform output
```

```shell
terraform output pet-name
```
