## Multiple Provider

### `main.tf`

```terraform
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

- There are two resources
- `local` and `random`
