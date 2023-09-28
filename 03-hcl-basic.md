## HCL Basic

### Basic Structure

```
<block> <parameters> {
    key1 = value1
    key2 = value2
}
```

### Example

#### Make Directory

```shell
mkdir terraform-local-file
cd terraform-local-file
```

#### Make `local.tf`

```terraform
resource local_file pet {
  filename = "/root/pets.txt"
  content  = "We love pets!"
}
```

- `resource`: Block name
- `local_file`: Resource Type
- `local`: Provider
- `file`: Resource
- `filename = "/root/pets.txt"`: Argument
- `content = "We love pets!"`: Argument

### AWS Example

#### EC2 - `aws-ec2.tf`

```terraform
resource aws_instance webserver {
  ami           = "ami-0c2f25c1f55"
  instance_type = "t2.micro"
}
```

#### S3 Bucket - `aws-s3.tf`

```terraform
resource aws_s3_bucket data {
  bucket = "webserver-bucket-org-2023"
}
```

### Terraform Commands

#### Terraform Init

```shell
terraform init
```

#### Terraform Plan

```shell
terraform plan
```

#### Terraform Apply

```shell
terraform apply
```

#### Terraform Destroy

```shell
terraform destroy
```
