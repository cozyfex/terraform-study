## Resource Attributes

Focus `${random_pet.my-pet.id}`

```terraform
# main.tf

resource local_file pet {
  filename = "/root/pets.txt"
  content  = "My favorite pet is ${random_pet.my-pet.id}"
}

resource random_pet my-pet {
  prefix    = "Mr"
  separator = "."
  length    = 2
}
```
