## Understanding Variable Block

### Variable Structure

```terraform
# variables.tf

variable filename {
  default     = "/root/pets.txt"
  type        = string
  description = "the path of local file"
}
variable length {
  default     = 2
  type        = number
  description = "length of the pet name"
}
variable password_change {
  default = true
  type    = bool
}
```

### Variable Types

| Type   | Example                   |
|--------|---------------------------|
| string | "/root/pets.txt"          |
| number | 1                         |
| bool   | true/false                |
| any    | Default Value             |
| list   | ["cat", "dog" ]           |
| map    | pet1 = cat<br/>pet2 = dog |
| object | Complex Data Structure    |
| tuple  | Complex Data Structure    |

### List Example

```terraform
# variables.tf

variable prefix {
  default = ["Mr", "Mrs", "Sir"]
  type    = list(string)
}
```

```terraform
# main.tf

resource random_pet my-pet {
  prefix = var.prefix[0]
}
```

### Map Example

```terraform
# variables.tf

variable file-content {
  type    = map(string)
  default = {
    "statement1" = "We love pets!"
    "statement2" = "We love animals!"
  }
}
variable length {
  type    = map(number)
  default = {
    "length1" = 1
    "length2" = 2
  }
}
```

```terraform
# main.tf

resource local_file my-pet {
  filename = "/root/pets.txt"
  content  = var.file-content["statement2"]
}
resource random_pet pet-id {
  prefix    = "Mrs"
  separator = "."
  length    = var.length["length2"]
}
```

### Set Example

```terraform
# variables.tf

variable prefix {
  type    = set(string)
  default = ["Mr", "Mrs", "Sir"]
}
variable prefix-wrong {
  type    = set(string)
  default = ["Mr", "Mrs", "Sir", "Mr"] # Wrong
}
```

### Object Example

```terraform
# variables.tf

variable bella {
  type = object({
    name         = string
    color        = string
    age          = number
    food         = list(string)
    favorite_pet = bool
  })
  default = {
    name         = "bella"
    color        = "brown"
    age          = 11
    food         = ["fish", "chicken", "turkey"]
    favorite_pet = true
  }
}
```

### Tuple Example

```terraform
# variables.tf

variable kitty {
  type    = tuple([number, bool, string])
  default = [10, true, "test"]
}
```
