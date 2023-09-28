## Resource Dependencies

### Implicit Dependency(Reference expression)

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

### Explicit Dependency

```terraform
# main.tf

resource local_file pet {
  filename   = "/root/pets.txt"
  content    = "My favorite pet is ${random_pet.my-pet.id}"
  depends_on = [
    random_pet.my-pet
  ]
}

resource random_pet my-pet {
  prefix    = "Mr"
  separator = "."
  length    = 2
}
```
