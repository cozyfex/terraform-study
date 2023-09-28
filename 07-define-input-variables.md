## Define Input Variables

### Example

```terraform
# main.tf

resource local_file pet {
  filename = "/root/pets.txt"
  content  = "We love pets!"
}

resource random_pet my-pet {
  prefix    = "Mrs"
  separator = "."
  length    = 1
}
```

| Argument  | Value            |
|-----------|------------------|
| filename  | "/root/pets.txt" |
| content   | "We love pets!"  |
| prefix    | "Mrs"            |
| separator | "."              |
| length    | 1                |

### Variables Example 1

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
  content  = var.content
}

resource random_pet my-pet {
  prefix    = var.prefix
  separator = var.separator
  length    = var.length
}
```

### Variables Example 2

```terraform
# variables.tf

variable "ami" {
  default = "ami-1110202030"
}
variable "instance_type" {
  default = "t2.micro"
}
```

```terraform
# main.tf

resource "aws_instance" "webserver" {
  ami           = var.ami
  instance_type = var.instance_type
}
```
